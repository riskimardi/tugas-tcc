TUTORIAL MEMBUAT DOCKER SWARM
 Docker Swarm
Docker Swarm adalah pengelompokan dan penjadwalan alat untuk kontainer Docker. Dengan Swarm, 
administrator TI dan pengembang dapat membangun dan mengelola cluster node Docker sebagai sistem virtual tunggal.

Buat manager dan worker machine

    docker-machine create --driver virtualbox manager
    docker-machine create --driver virtualbox worker

cek machine yang telah dibuat

    docker-machine ls

 Mulai mesin dengan alamat IP baru

    docker-machine env manager

Jalankan perintah ini untuk mengkonfigurasi shell

    eval "$(docker-machine env manager)"

SSH ke machine manager

    docker-machine ssh manager

docker swarm init --advertise-addr <MANAGER-IP>

    contoh : docker swarm init --advertise-addr 192.168.99.100

 docker@manager:~$ docker swarm init --advertise-addr 192.168.99.100
Swarm initialized: current node (2tjrasfqfu945b7n4753374sw) is now a manager.

To add a worker to this swarm, run the following command:

docker swarm join \
--token SWMTKN-1-144pfsupfo25h43zzr6b6bghjson8uedxjsndo5vuehqlyarsk-9k4q84axm008whv9zl4a8m8ct \
192.168.99.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.


SSH ke machine worker

    docker-machine ssh worker

Join ke machine manager

    docker swarm join \
    > --token SWMTKN-1-144pfsupfo25h43zzr6b6bghjson8uedxjsndo5vuehqlyarsk-9k4q84axm008whv9zl4a8m8ct \
    > 192.168.99.100:2377

List node

    docker node ls
