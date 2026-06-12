---
title: "ssh keygen"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-21
I set up the public key using:
Client: ssh-keygen -q -f ~/.ssh/id_rsa -t rsa
Server: scp ~/.ssh/id_rsa.pub server
           cat ~/id_rsa.pub >> ~/.ssh/authorized_keys

Now from the client, if I do ssh server, I can connect without entering, but when I do it from the following script as sudo, it asks me for the password. Any Ideas?


#!/bin/sh

SUFFIX=`date +%s`
DEVICE=/dev/sda
HOSTNAME="$(cat /etc/hostname)"
SERVER=o1
BLKTR_FILE="/tmp/$HOSTNAME-$SUFFIX"
USERNAME=medha

do_start () {
        echo "Starting blktrace..."
        echo  $USERNAME
        echo $SERVER
       (/usr/sbin/blktrace -d $DEVICE -o - | ssh $USERNAME@$SERVER "cat > $BLKTR_FILE") &
        echo "Done"
}
case "$1" in
  start|"")
        do_start
        ;;
  restart|reload|force-reload)
       echo "Error: argument '$1' not supported" >&2
       exit 3
       ;;
 stop)
       pkill -15 blktrace
       ;;
 *)
       echo "Usage: start-blktrace.sh [start|stop]" >&2
       exit 3
       ;;
esac

---

### Post by RealPSL on 2008-03-22
You hint that you are running the script as sudo but it does not sound that what you copied to the remote server is the root ssh public key. 

To confirm test running this sudo ssh remote_server if my suspicions are correct you will be prompted for a password. I believe what you setup is to connect to the remote machine as yourself with your ssh keys. However once you put sudo infront of the script it runs everything in that script as root including the ssh commands which is why the remote connection is prompting for a password.

---

