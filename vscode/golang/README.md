# docker-code
Development Environments

Install XQuartz 

```
brew cask install xquartz
```

Open XQuartz and all connections from network clients

```
open -a XQuartz
```

Allow connections from your local machine 

```
ip=$(ifconfig en0 | grep inet | awk '$1=="inet" {print $2}')
xhost + $ip
```

Build
```
docker build -t prizyp/golang .
```

Run
```
docker run -it -d -v <user-data>:/user-data -v <workspace>:/workspace -v $HOME:/root --net=host --privileged -e DISPLAY=$ip:0 -v /tmp/.X11-unix:/tmp/.X11-unix prizyp/golang
```

Yes I know that vscode doesn't like being run as root - but your in a container - Live a little :)

Create an alias from the script included in this repository: go.sh
