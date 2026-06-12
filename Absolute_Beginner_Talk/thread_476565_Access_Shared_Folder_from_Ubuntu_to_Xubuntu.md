---
title: "Access Shared Folder from Ubuntu to Xubuntu"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by MichiganMan on 2007-06-17
I just set up an Xubuntu box and want to read and write to a folder on it from my Ubuntu system.  

On the Xubuntu I set up a shared folder with the IP address of my Ubuntu system .  Thinking that I am going Linux to Linux I only installed the Unix Network file sharing, not Samba.  Is this wrong?  

In any case, using the Network Bowser in Ubuntu, I can't see the shared folder on the Xubuntu system.  Am I missing something?  Thank you for any help.

---

### Post by meborc on 2007-06-17
i know that this should work - [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

edit:

i copied this from another thread (u.b.u.n.t.u)> There are 3 stages.

1. Download the software on both machines, server and client.
2. Set up the server.
3. Set up the client.

* Set up the server.
[path location to what is being shared] [IP of client][permissions]
"/home/czar/tmp 192.168.1.1/24(rw,no_root_squash,async)"

* Set up the client.
You need to make a directory that will access the server.
[mount IP of server : path location of what is being shared] ~/[mount in this directory]
"sudo mount 192.168.1.2:/media/hdc5/music ~/music"

* Three things to remember.
The server needs the client IP.
The client needs the server IP.
Make sure the server firewall allows the client IP access.

---

