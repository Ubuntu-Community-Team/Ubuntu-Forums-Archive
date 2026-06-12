---
title: "help needed can`t install virtual box on ubuntu 7.10"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Nedux on 2007-10-25
I got this package virtualbox_1.5.2-25433_Ubuntu_gutsy_i386 and I need to install it ,` Please tell me how `, I`m a noob . yesterday` I Instaled ubuntu and I realy like `,
I got a second issue . hmm ,. after I will install virtual box., I want to install windows on it and inside windows i want to install ps Cs2, illustrator Cs2 and flash. I realy don`t know if this aplications will work well , please help :)

---

### Post by captaink on 2007-10-25
Why don't you install the OpenSource edition of Virtualbox from the repos? Open a terminal and type ```
sudo apt-get install virtualbox-ose
```. 
You can use wine also. Have you tried installing your windows apps with wine? I think photoshop runs smoothly, unless I 'm mistaken. Check [http://appdb.winehq.org]("http://appsdb.winehq.org") to see if and how your applications work.

About the second issue. When creating the Virtual Machine, choose to have enough memory. I think 512 or better 1024 will do the job. Make sure you have more than this amount on your PC. Do you have enough RAM?

---

### Post by n3tfury on 2007-10-25
to run those adobe apps in virtualbox (or any vm for that matter) you should have at LEAST 1GB of RAM.

---

### Post by Nedux on 2007-10-25
```
nedu@nedu-zen:~$ sudo apt-get install virtualbox-ose
[sudo] password for nedu:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose

```

it won`t work this way,

yes I got 1gb ram.

---

### Post by n3tfury on 2007-10-25
some things changed for 7.10 for installation.  look here:

[http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/12/how-to-install-virtualbox-open-source-edition-on-ubuntu-710/)

---

### Post by Maestro23 on 2007-10-25
> **Nedux said:**
> ```
nedu@nedu-zen:~$ sudo apt-get install virtualbox-ose
[sudo] password for nedu:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose

```

it won`t work this way,

yes I got 1gb ram.

You need to enable your Universe and Multiverse Repositories.

System>>Admin>>Software Sources

---

### Post by n3tfury on 2007-10-25
hiya maestro

---

### Post by Maestro23 on 2007-10-25
> **n3tfury said:**
> hiya maestro

How's it going n3t :)

---

### Post by PartisanEntity on 2007-10-25
I installed VB manually from their website, it is working fine on Gutsy.

I would just like to point out that running Photoshop in VB with 512MB is absolutely no problem. Even though I have 2GB of RAM, I gave the virtual machine only 512MB and I have not had any issues.

---

### Post by Nedux on 2007-10-25
```
nedu@nedu-zen:~$ sudo apt-get install virtualbox-ose
[sudo] password for nedu:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27
  virtualbox-ose-modules-2.6.22-14-generic
Suggested packages:
  nas libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc xalan
Recommended packages:
  virtualbox-ose-source
The following NEW packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27 virtualbox-ose
  virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After unpacking 37.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]
Get:2 http://archive.ubuntu.com gutsy/main libqt3-mt 3:3.3.8really3.3.7-0ubuntu11 [3299kB]
Get:3 http://archive.ubuntu.com gutsy/universe libxerces27 2.7.0-3 [1321kB]    
Get:4 http://archive.ubuntu.com gutsy/universe libxalan110 1.10-3.1 [1241kB]   
Get:5 http://archive.ubuntu.com gutsy/universe virtualbox-ose-modules-2.6.22-14-generic 6 [317kB]
Get:6 http://archive.ubuntu.com gutsy/universe virtualbox-ose 1.5.0-dfsg2-1ubuntu3 [5695kB]
Fetched 12.0MB in 1m37s (123kB/s)                                              
Selecting previously deselected package libaudio2.
(Reading database ... 88976 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9-2_i386.deb) ...
Selecting previously deselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu11_i386.deb) ...
Selecting previously deselected package libxerces27.
Unpacking libxerces27 (from .../libxerces27_2.7.0-3_i386.deb) ...
Selecting previously deselected package libxalan110.
Unpacking libxalan110 (from .../libxalan110_1.10-3.1_i386.deb) ...
Selecting previously deselected package virtualbox-ose-modules-2.6.22-14-generic.
Unpacking virtualbox-ose-modules-2.6.22-14-generic (from .../virtualbox-ose-modules-2.6.22-14-generic_6_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.0-dfsg2-1ubuntu3_i386.deb) ...
Setting up libaudio2 (1.9-2) ...

Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11) ...

Setting up libxerces27 (2.7.0-3) ...

Setting up libxalan110 (1.10-3.1) ...

Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                    chown: `:vboxusers': invalid group

 * Cannot change owner vboxusers for device /dev/vboxdrv.

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nedu@nedu-zen:~$ 

```

stil not working ,. hmm . how can I install manualy ? or what should I do `?


and i don`t wanna ` get back to windows `,. beah` ..
Probably after installing this all my problems will be solved` ,. I realy need to get ps and illustrator installed . I got projects that must be done before dedline :( and I`m tryn to set up this for 2 days `,


oh `.:D just checked now and Virtual Box was instaled .:D

how much ram should I allocate to virtual machine ?

---

### Post by n3tfury on 2007-10-25
> **PartisanEntity said:**
> I installed VB manually from their website, it is working fine on Gutsy.

I would just like to point out that running Photoshop in VB with 512MB is absolutely no problem. Even though I have 2GB of RAM, I gave the virtual machine only 512MB and I have not had any issues.

when i said at least 1GB, i was talking about the host :)

OP: that looked like it installed correctly..

---

### Post by PartisanEntity on 2007-10-25
> **n3tfury said:**
> when i said at least 1GB, i was talking about the host :)

Oh sorry, misunderstood you :)

---

### Post by Maestro23 on 2007-10-25
> **Nedux said:**
> ```
nedu@nedu-zen:~$ sudo apt-get install virtualbox-ose
[sudo] password for nedu:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27
  virtualbox-ose-modules-2.6.22-14-generic
Suggested packages:
  nas libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc xalan
Recommended packages:
  virtualbox-ose-source
The following NEW packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27 virtualbox-ose
  virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.0MB of archives.
After unpacking 37.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]
Get:2 http://archive.ubuntu.com gutsy/main libqt3-mt 3:3.3.8really3.3.7-0ubuntu11 [3299kB]
Get:3 http://archive.ubuntu.com gutsy/universe libxerces27 2.7.0-3 [1321kB]    
Get:4 http://archive.ubuntu.com gutsy/universe libxalan110 1.10-3.1 [1241kB]   
Get:5 http://archive.ubuntu.com gutsy/universe virtualbox-ose-modules-2.6.22-14-generic 6 [317kB]
Get:6 http://archive.ubuntu.com gutsy/universe virtualbox-ose 1.5.0-dfsg2-1ubuntu3 [5695kB]
Fetched 12.0MB in 1m37s (123kB/s)                                              
Selecting previously deselected package libaudio2.
(Reading database ... 88976 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9-2_i386.deb) ...
Selecting previously deselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8really3.3.7-0ubuntu11_i386.deb) ...
Selecting previously deselected package libxerces27.
Unpacking libxerces27 (from .../libxerces27_2.7.0-3_i386.deb) ...
Selecting previously deselected package libxalan110.
Unpacking libxalan110 (from .../libxalan110_1.10-3.1_i386.deb) ...
Selecting previously deselected package virtualbox-ose-modules-2.6.22-14-generic.
Unpacking virtualbox-ose-modules-2.6.22-14-generic (from .../virtualbox-ose-modules-2.6.22-14-generic_6_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.0-dfsg2-1ubuntu3_i386.deb) ...
Setting up libaudio2 (1.9-2) ...

Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11) ...

Setting up libxerces27 (2.7.0-3) ...

Setting up libxalan110 (1.10-3.1) ...

Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                    chown: `:vboxusers': invalid group

 * Cannot change owner vboxusers for device /dev/vboxdrv.

Setting up virtualbox-ose (1.5.0-dfsg2-1ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nedu@nedu-zen:~$ 

```

stil not working ,. hmm . how can I install manualy ? or what should I do `?


and i don`t wanna ` get back to windows `,. beah` ..
Probably after installing this all my problems will be solved` ,. I realy need to get ps and illustrator installed . I got projects that must be done before dedline :( and I`m tryn to set up this for 2 days `,


oh `.:D just checked now and Virtual Box was instaled .:D

how much ram should I allocate to virtual machine ?

Looks like the install went good. The above poster gave you a suggestion on RAM allocation.

Here's a link to the User's Manual: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Good luck man and have fun.:guitar:

---

### Post by n3tfury on 2007-10-25
> **PartisanEntity said:**
> Oh sorry, misunderstood you :)

probably because i wasn't clear enough, my fault ;)

have fun with VB nedux.

---

