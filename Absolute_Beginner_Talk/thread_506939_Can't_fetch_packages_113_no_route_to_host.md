---
title: "Can't fetch packages: 113 no route to host"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by original_jamingrit on 2007-07-22
I can't download the boost libraries, which I need to install the deluge deb package.  I'm pretty sure the boost libraries are in the normal ubuntu universe repository.

I recieved some updates earlier this morning, would that have something to do with it?  Or is it just a connection problem?

---

### Post by original_jamingrit on 2007-07-22
Here's what it looks like.

```
[11:31:42]~$ sudo apt-get install libboost-filesystem1.33.1 libboost-date-time1.33.1 libboost-thread1.33.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-thread1.33.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 158kB of archives.
After unpacking, 586kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-thread1.33.1
Install these packages without verification [y/N]? y
Err http://ca.archive.ubuntu.com feisty/universe libboost-date-time1.33.1 1.33.1-9ubuntu3
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe libboost-filesystem1.33.1 1.33.1-9ubuntu3
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe libboost-thread1.33.1 1.33.1-9ubuntu3
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-date-time1.33.1_1.33.1-9ubuntu3_i386.deb Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-filesystem1.33.1_1.33.1-9ubuntu3_i386.deb Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/boost/libboost-thread1.33.1_1.33.1-9ubuntu3_i386.deb Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```

---

### Post by original_jamingrit on 2007-07-22
As an experiment, I tried downloading two packages through synaptic, one from ubuntu and one from medibuntu.  I could download the medibuntu one, but not the ubuntu one.

???

---

### Post by original_jamingrit on 2007-07-22
Never mind, it should be okay now.  Maybe the ubuntu servers for Canada are down.  I switched to the ubuntu main servers for now.  Can access the repositories as normal, now.

---

### Post by r0n on 2007-07-22
How do you change to main ubuntu servers?

---

### Post by ThrobbingBrain66 on 2007-07-22
Yes there are problems with the Canada servers right now.

[http://ubuntuforums.org/showthread.php?t=506996](http://ubuntuforums.org/showthread.php?t=506996)
[http://ubuntuforums.org/showthread.php?t=504193](http://ubuntuforums.org/showthread.php?t=504193)

@r0n:
System>Adminstration>Software Sources

then change the 'Download from' box from Canada to Main

---

### Post by Rosemere on 2007-07-23
does that mean what I was doing above was correct. 

I changed the server to Main.:confused:

---

