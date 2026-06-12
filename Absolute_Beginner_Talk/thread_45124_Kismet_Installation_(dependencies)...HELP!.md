---
title: "Kismet Installation (dependencies)...HELP!"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by jabaman21 on 2005-06-28
I am wanting to install kismet, but everytime I tried, I got a message saying that "libgmp3, ethereal-common, libglib1.2, libpcre3" have to be installed because they are dependencies....

So, I typed the command to install all of them, and I got this message....




root@VOORHEES:~# sudo apt-get install libgmp3 ethereal-common libglib1.2 libpcre3
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  ethereal tethereal
The following NEW packages will be installed:
  ethereal-common libglib1.2 libgmp3 libpcre3
0 upgraded, 4 newly installed, 0 to remove and 50 not upgraded.
1 not fully installed or removed.
Need to get 4475kB/5017kB of archives.
After unpacking 18.6MB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter




Where do I get the 5.04_Hoary Hedgehog_-Release i386 from to download so that I can burn it to a cd...?

Is there anything else that I should do or know that will help me?

Please help.....

---

### Post by jasmuz on 2005-06-28
[QUOTE=jabaman21]I am wanting to install kismet, but everytime I tried, I got a message saying that "libgmp3, ethereal-common, libglib1.2, libpcre3" have to be installed because they are dependencies....

So, I typed the command to install all of them, and I got this message....




root@VOORHEES:~# sudo apt-get install libgmp3 ethereal-common libglib1.2 libpcre3
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  ethereal tethereal
The following NEW packages will be installed:
  ethereal-common libglib1.2 libgmp3 libpcre3
0 upgraded, 4 newly installed, 0 to remove and 50 not upgraded.
1 not fully installed or removed.
Need to get 4475kB/5017kB of archives.
After unpacking 18.6MB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter




Where do I get the 5.04_Hoary Hedgehog_-Release i386 from to download so that I can burn it to a cd...?

Is there anything else that I should do or know that will help me?

Please help.....[/QUOTE]
 First off...its asking you for the Ubuntu Cd you used to install the base system.

I recommend you modify your sources.list accordingly to the [www.ubuntuguide.org](www.ubuntuguide.org)

If you have any other question please post, and why do you want kismet?

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=jabaman21]

Is there anything else that I should do or know that will help me?

Please help.....[/QUOTE]

I know what you need. This:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then this command:

sudo apt-get update 

to aplly the changes made....then try again.

---

