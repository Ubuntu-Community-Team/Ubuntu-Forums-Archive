---
title: "installing net6vpn"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by raves71 on 2007-06-21
I'm having a bt of a problem installing the net6vpn client on ubuntu 7.04

I'm useing a root konsol - I've done a chmod +x on the install script and am getting the following output:

 Determining distribution... detected Linux--unknown.
Unpacking (17754+1110399+23=1128176)...
1110422
Checksumming...
0
0
Extracting...
Installing...
./citrixvpn-linux-2.4-i386.sh: 383: /etc/init.d/net6vpnd: not found
install: cannot stat `/tmp/.net6/net6vpnd': No such file or directory
install: cannot stat `/tmp/.net6/net6vpnd..init': No such file or directory
install: cannot stat `/tmp/.net6/net6vpn': No such file or directory
Installing ip_queue kernel module...
gcc: /tmp/.net6/ip_queue.c: No such file or directory
gcc: no input files
Adding net6vpnd to default runlevel...
Starting daemon
./citrixvpn-linux-2.4-i386.sh: 416: /etc/init.d/net6vpnd: not found
Cleaning up...
Done.
root@scubuntu:/home/stuartc/Desktop/Stuff# net6vpn
net6vpn: net: socket: socket hung up.
net6vpn: failed to connect to daemon. [Operation now in progress]
net6vpn: failed to do network io.
net6vpn: failed to get connection id.

 now I'm a beginner and I have no idea what that means - any ideas?

 Thanks in advance :)

 ** Aditional info - I was messing around with symbolic links in order ot install VMware workstation 6, but unfortunately I'm not sure exactly what I did as I was just following a guide :s Vmware workstation works though :)

---

