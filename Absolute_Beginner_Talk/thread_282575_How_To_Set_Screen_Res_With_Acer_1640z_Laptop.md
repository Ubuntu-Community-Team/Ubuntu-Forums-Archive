---
title: "How To Set Screen Res With Acer 1640z Laptop"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-22
Removed due to another member supplying superior information. I have included this.

---

### Post by ReaderRat on 2006-10-22
Sorry, No bad feelings I hope....just trying to help.

---

### Post by unlokia on 2006-10-22
Cool it's much appreciated, as was your help :)

---

### Post by ramjet_1953 on 2006-10-23
Why go through all of that command line stuff, when 915resolution is available for download with Synaptic?

Roger :-D

---

### Post by unlokia on 2006-10-23
Still need to configure it though!!

---

### Post by ramjet_1953 on 2006-10-23
No, just run it!
It does the alterations to the necessary files automatically.
Did for me, anyway.

Roger

---

### Post by unlokia on 2006-10-23
Oh okay - hmmm :-k didn't realise that. Thanks for the feedback!.

Here is what I did with liveCD and yes you were right! :D

```
ubuntu@ubuntu:~$ sudo gedit /etc/apt/sources.list
ubuntu@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [189B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US         
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US   
Hit http://security.ubuntu.com edgy-security Release  
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/main Translation-en_US
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://archive.ubuntu.com edgy Release [34.7kB]
Get:4 http://security.ubuntu.com edgy-security/main Packages [14B]
Get:5 http://archive.ubuntu.com edgy/main Packages [939kB]
Get:6 http://security.ubuntu.com edgy-security/restricted Packages [14B]
Get:7 http://security.ubuntu.com edgy-security/main Sources [14B]        
Get:8 http://security.ubuntu.com edgy-security/restricted Sources [14B]  
Get:9 http://archive.ubuntu.com edgy/restricted Packages [5974B]         
Get:10 http://archive.ubuntu.com edgy/main Sources [274kB]
Get:11 http://archive.ubuntu.com edgy/restricted Sources [1436B]
Get:12 http://archive.ubuntu.com edgy/universe Packages [3557kB]
Get:13 http://archive.ubuntu.com edgy/universe Sources [1068kB]                
Fetched 5881kB in 11s (504kB/s)                                                
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/universe 915resolution 0.5.2-4ubuntu1 [15.1kB]
Fetched 15.1kB in 0s (57.6kB/s) 
Selecting previously deselected package 915resolution.
(Reading database ... 92259 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-4ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-4ubuntu1) ...
Starting 915resolution: Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 3c to resolution 1280x800 complete
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 4d to resolution 1280x800 complete
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 5c to resolution 1280x800 complete
915resolution.

ubuntu@ubuntu:~$ 

```

---

