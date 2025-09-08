# BloodHound Docker Ready to Use

This is the old bloodhound. Standalone and fully functional. Not Community Edition (CE).

[BloodHound](https://github.com/BloodHoundAD/BloodHound) Docker image out of the box, with collectors and [tons of custom queries](https://github.com/CompassSecurity/BloodHoundQueries/blob/master/BloodHound_Custom_Queries/customqueries.json). It creates a `bh-data` folder with the Ingestors, the data folder is also mounted as a volume, use this to drop your data and load it into the BloodHound GUI.

![bloodhound](https://user-images.githubusercontent.com/17031267/48985201-6f587a00-f105-11e8-8355-98e38e08cc5e.png)


## Build Image
Clone this repo
```
git clone https://github.com/t4x0r-toolbox/bloodhound-legacy-docker
```

### Recommended Arguments
```
docker build . -t bloodhound --build-arg neo4j=4.4.15 --build-arg bloodhound=4.2.0`
```
- **neo4j** version
- **bloodhound** version

(you can also run it as)
`docker build . -t bloodhound`


### Run
Warning: You may need to run `xhost +local:$(id -nu)` to allow the local user to access DISPLAY before running it.

```
docker run -it \
  -p 7474:7474 \
  -e DISPLAY=unix$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  --device=/dev/dri:/dev/dri \
  -v $(pwd)/bh-data:/data \
  --name bloodhound bloodhound
```

## Start container

`docker start bloodhound`

## Database Login

- **DB URL:** bolt://localhost:7687
- **DB Username:** neo4j
- **DB Password:** blood

## Documentation
--- They have removed the documentation from bloodhound(dot)readthedocs(dot)io, it no longer works. If you find it a different place for it, please let me know and I'll add the link. ---


Thanks FacundoIC for showing me this.
Thanks @belane for the original repo and dockerfile.
