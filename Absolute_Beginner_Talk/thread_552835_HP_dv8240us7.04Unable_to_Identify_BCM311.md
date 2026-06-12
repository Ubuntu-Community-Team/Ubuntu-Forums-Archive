---
title: "HP dv8240us/7.04/Unable to Identify BCM311"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by hexoic on 2007-09-17
I have an issue with my corresponding **Broadcom BCM3311 WLAN-card**. Ubuntu doesn't identify it. 

I'm using a **HP Pavillion dv8240us laptop** with Ubuntu 7.04 Fiesty Fawn currently installed. The laptop has no Ethernet input connectors, in fact much of my problem has been because of this issue.Most of the tutorials I've tried, require me to be connected to the internet through a lan line.  Of course this is impossible with my current setup and has been giving me stress trying to find the solution. 

I'm able to use a pocket USB drive to transfer files from my PC Computer which has internet to my laptop which doesn't. 

All help is appreciated.

---

### Post by Bachstelze on 2007-09-17
Well, all you have to do that requires an Internet connection is installing a few packages, which can be downloaded on another machine and installed manually. Which tutorials are you trying to follow ?

---

### Post by hexoic on 2007-09-17
WifiDocs/Device/Broadcom BCM4311 rev 01 (ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

I get stuck when I'm required to install the essential builds to compile my driver.  

The instruction looks like this:

```
user@ubuntu:~$ sudo apt-get update
user@ubuntu:~$ sudo apt-get install build-essential
```

---

### Post by hexoic on 2007-09-17
Is there a way I can download the essentials from my PC and then transfer it to my laptop?

---

### Post by Maestro23 on 2007-09-17
> **hexoic said:**
> Is there a way I can download the essentials from my PC and then transfer it to my laptop?

You can get all the packages (+ their dependencies) from Ubuntu Packages.  Save them to a flash drive, cd, etc..  Then fire up Ubuntu and copy the files.

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by hexoic on 2007-09-17
> **Maestro23 said:**
> You can get all the packages (+ their dependencies) from Ubuntu Packages.  Save them to a flash drive, cd, etc..  Then fire up Ubuntu and copy the files.

Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I'm using Fiesty Fawn 7.04, therefore I selected the fiesty link ([http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)). I also noticied a "feisty-backports", what is this? 

The link provides me with a vast amount of packages. I'm confused which packages should I download. Also another thing, since I'm going to be transferring the package from PC Computer to my laptop, will I  be required to use any terminal commands to install them? or do I just simply double click them and install?

---

### Post by hexoic on 2007-09-17
^Bump

---

### Post by mocoloco on 2007-09-17
[Here's what you want]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/").
If you're using Windows to download it you can't just run the script, but you can open it with a text edit (notepad, etc) and just copy-past the URLs to download everything you need.

---

### Post by Maestro23 on 2007-09-17
> **mocoloco said:**
> [Here's what you want]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/").
If you're using Windows to download it you can't just run the script, but you can open it with a text edit (notepad, etc) and just copy-past the URLs to download everything you need.


Cool link.  That goes in my bookmarks. :)

---

