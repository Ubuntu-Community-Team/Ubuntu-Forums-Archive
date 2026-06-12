---
title: "apt-get problem"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Orta on 2006-06-02
Hello all. I've successfully installed Ubuntu 6.06. I even managed to fix my stretched resolution problem with the help of the forums, thanks. :D However, I want to download a few packages to add multimedia capabilities (dvd, mp3, etc.) and also **vpnc** for connecting to my school's wireless network. apt-get doesn't seem to be working with me.

I have tried both **sudo apt-get update** and **sudo apt-get upgrade** with the following outputs:

```
sudo apt-get update

Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:2 http://au.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://au.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://au.archive.ubuntu.com dapper Release
Hit http://au.archive.ubuntu.com dapper-updates Release
Hit http://au.archive.ubuntu.com dapper/main Packages
Hit http://au.archive.ubuntu.com dapper/restricted Packages
Hit http://au.archive.ubuntu.com dapper/main Sources
Hit http://au.archive.ubuntu.com dapper/restricted Sources
Hit http://au.archive.ubuntu.com dapper-updates/main Packages
Hit http://au.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://au.archive.ubuntu.com dapper-updates/main Sources
Hit http://au.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done
``` 

```
sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So, apparently, apt-get is connecting to the internet. That doesn't seem to be an issue anyway since I'm posting this from Firefox. My problem is when I try to get the packages. For instance, 

```
sudo apt-get install vpnc
```
outputs...
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vpnc
```

This also happens with a number of packages from ubuntuguide.org. What am I missing here? I read something about extra package repositories... Where can I find such a list (the most complete possible, if possible)? Thanks for your kind help.

---

### Post by edwina on 2006-06-02
Look here, under the Universe and Multiverse link: [http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by tonyr on 2006-06-02
...and here's another one...
[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

---

### Post by johnc4510 on 2006-06-02
Do this to enable extra repositories:
System>Administration>Synaptic Package Manager
Click on Settings, Click on Repositories
Put a check mark in all empty boxes and close window
Click on Reload, Click on Mark all Upgrades, Click on Apply
The extra apps should be in the synaptic window ready to download

---

### Post by diesel4555 on 2006-08-16
johnc4510

This was the best suggestion I have gotten so far.  Thanks!

Diesel

---

### Post by sailor2001 on 2006-08-16
> **diesel4555 said:**
> johnc4510

This was the best suggestion I have gotten so far.  Thanks!

Diesel
some programs do not install direct to your aplication menu and you have to click on places/home folder/ctrl-h and locate the install from there .I also copy & paste an icon from that on the desktop and sometimes, if it will be used enough, paste on the top panel

---

### Post by jive_turkey on 2006-08-16
You should also be able to edit the menu items using the Alacarte Menu Editor, and if you are using 6.06 it should be installed by default.

---

