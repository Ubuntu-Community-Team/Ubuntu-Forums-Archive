---
title: "Trouble installing an application."
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Ric95 on 2006-04-07
I found my favorite app.(Blender)  in the Synaptic installer, so i tried to add it. It seemed ok, but I think only some configuration files installed, not the program. I downloaded the Blender.tar.gz , but it only wants to unpack into the 'system files' folder. 
How can I manually install this ?
( I'm not sure if synaptic would have picked the 64 bit vers I want anyhow.)

---

### Post by aysiu on 2006-04-07
The 64 version is [right here in the main repositories](http://security.ubuntu.com/ubuntu/pool/main/b/blender/blender_2.37a-1ubuntu1.1_amd64.deb). Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install blender
blender
```

---

### Post by Ric95 on 2006-04-09
When I updated, it got 18 update files.:)
I removed the empty Blender install I had, then;
ric@ubuntu:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  yafray
The following NEW packages will be installed
  blender
0 upgraded, 1 newly installed, 0 to remove and 184 not upgraded.
Need to get 0B/5400kB of archives.
After unpacking 14.4MB of additional disk space will be used.
Selecting previously deselected package blender.
(Reading database ... 67491 files and directories currently installed.)
Unpacking blender (from .../blender_2.41-1ubuntu4_amd64.deb) ...
Setting up blender (2.41-1ubuntu4) ...
ric@ubuntu:~$ blender
Using Python version 2.4
ERROR: Unable to open Blender window

Still an empty install.:(
But I do have the Shortcut icon on the top bar. I have set its properties/command box to the .exe location. Still no luck. :(

---

### Post by Ric95 on 2006-04-18
After reading other forums it looks like most others are having this problem too.
Are there dependencies synaptic missed ?
Has anyone here successfully installed Blender (2.41/64bit)?

---

