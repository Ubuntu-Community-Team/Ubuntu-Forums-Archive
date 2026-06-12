---
title: "nfs/cups server suddenly inaccessible"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-05-05
hello,

running dapper on both laptop and home desktop. desktop is my nfs server, and cups server.

after upgrading to feisty, then reinstalling dapper, i can't get access to the server- no nfs, no cups, no vncviewer...

unless i'm connected by cable. as far as i know, i haven't done anything on the server that would affect this. i've tried messing around with the server's /etc/exports file; here is its current state, which i believe should open up /home/steve to any computer in the 192.168.1.x pool:

```

# /etc/exports: the access control list for filesystems which may be exported # to NFS clients. See exports(5). /home/steve 192.168.1.1/24(rw,no_root_squash)

```

	
here's some more info:

when i do the following from my wireless laptop:

```

sudo ifconfig eth1 192.168.1.7
```


i can access my server for cups/nfs/vncviewer, but cannot get onto the internet.

to do that, i have to do


```
sudo dhclient eth1
```


then i get a new address- 192.168.1.2, for example- and then i can get on the 'net but not to the home server.

there's something basic wrong here, but it seems to be eluding me for the moment...

	
still more info:

when i set ip addresses [with ifconfig] in the range of [192.168.1.]4-7, i have vncviewer access, but no internet access unless i'm connected with a wire.

if i want to get online, i have to use dhclient to request a new address- setting it with ifconfig doesn't work if i want internet access.

but i can't get both at the same time. any ideas?

-steve

---

### Post by eltorodeoro on 2007-05-08
the proper form for annotating a subnet like in your /etc/exports file is ```
192.168.1.0/24
```
this stands for 192.168.1.0 thru 192.168.1.255.  however, only 1-254 are actually usable.

when manually configuring your eth1, you are neglecting to dictate a default gateway (probably the 192.168.1.1 written into your /etc/exports code), leaving your computer no path to anything outside of its subnet.

let dhclient take care of that.  it's doing its job properly.  fix the line in /etc/exports and try it again.

---

### Post by stevieb on 2007-05-20
i fixed this line, but nfs still doesn't work unless my ip address is between 192.168.1.4 and .7.  in addition, changing this in /etc/exports did not fix the vncviewer or print server issues.

anything else to try?

-steve

---

