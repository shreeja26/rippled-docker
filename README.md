# The rippled Server
rippled is the core peer-to-peer server that manages the XRP Ledger. This section covers concepts that help you learn the "what" and "why" behind fundamental aspects of the rippled server.

# rippled Server Features
rippled Server Modes
Learn about rippled server modes, including stock servers, validator servers, and rippled servers run in stand-alone mode.

- Clustering
  - Run rippled servers in a cluster to share the load of cryptography between them.

- Ledger History
  - rippled servers store a variable amount of transaction and state history locally.

- Peer Protocol
 - The peer protocol specifies the language rippled servers speak to each other.

- Transaction Censorship Detection
 - XRP Ledger provides an automated transaction censorship detector that is available on all rippled servers.

# Rippled (node)
This container allows you to run a rippled node. No config required.

This container is running on ubuntu:latest.

# How to run

If you want to build the image manually, use (you can change the tag):

docker build --tag rippled:latest .
From the Docker Hub
Use the image shreeja/ripple.

Because you only retrieved the container image from the Docker Hub, you have to manually create a container based on the image. When creating the container, please make sure you open port 80.

This command launches your rippled container and the rippled websocket at port 80:

docker run -dit \
    --name rippled \
    shreeja/ripple:latest
You can change the --name.

You can fetch a working sample config from the Github repo.

# So it's running
If you want to check the rippled-logs (container stdout, press CTRL - C to stop watching):

docker logs -f rippled
If you want to check the rippled server status:

docker exec rippled server_info
Check the value of complete_ledgers in the server info to see if the server has complete ledgers with transactions. When you launch the container it may take a few minutes for the server to sync.

If you started the container manually, you may have to change the name of the container (rippled) to the name you entered in your docker run command.

# Connecting
You can now connect to the rippled websocket using a client like ripple-lib.

# Updating
2018-02-21 rippled 0.90.0 is released
2018-03-23 rippled 0.90.1 is released
2018-05-15 rippled 1.0.0 is released
2018-06-14 rippled 1.0.1 is released
2018-09-15 rippled 1.1.0 is released
2018-10-23 rippled 1.1.1 is released
2018-12-12 rippled 1.1.2 is released
2019-02-14 rippled 1.2.0 is released
2019-02-27 rippled 1.2.1 is released
2019-03-07 rippled 1.2.2 is released
2019-04-03 rippled 1.2.3 is released
2019-04-17 rippled 1.2.4 is released
2019-07-26 rippled 1.3.1 is released
2019-07-26 rippled 1.4.0 is released
2020-04-01 rippled 1.5.0 is released
2020-08-19 rippled 1.6.0 is released
2021-05-24 rippled 1.7.2 is released
2021-08-28 rippled 1.7.3 is released

# Update process
Stop the container: docker stop rippled (if you named (--name) the container rippled)
Remove the container: docker rm rippled
Remove the image: docker rmi shreeja/ripple:latest (or if you built the container image based on the Github repo: use the image name you specified when building)
Re-create the container; if you used Git: git pull and go/build - if you used the Docker Hub: just use the command from this Readme (From the Docker Hub), a new version of the image will be downloaded.
USE THE PATHS YOU SPECIFIED (-v argument) WHEN RECREATING THE CONTAINER IF YOU WANT TO KEEP YOUR CONFIG AND/OR DATA!
