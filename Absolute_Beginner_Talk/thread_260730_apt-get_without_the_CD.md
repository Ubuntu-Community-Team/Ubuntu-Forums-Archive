---
title: "apt-get without the CD"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jonnythan on 2006-09-19
I'm trying to install xubuntu-desktop on a fairly fresh LAMP server install. However, the server is in a remote location (my house) and the install CD is not in the drive. How do I tell apt-get to use ftp to get the packages?

---

### Post by Brunellus on 2006-09-19
> **jonnythan said:**
> I'm trying to install xubuntu-desktop on a fairly fresh LAMP server install. However, the server is in a remote location (my house) and the install CD is not in the drive. How do I tell apt-get to use ftp to get the packages?
in a word, you don't.

if it's got a network connection, it'll pull the packages off the repositories over the network.

sudo aptitude install xubuntu-desktop

will do it.

---

### Post by jonnythan on 2006-09-19
> **Brunellus said:**
> sudo aptitude install xubuntu-desktop

will do it.
I tried that, but it asks for the cd to be inserted:
```

Media Change: Please insert the disc labeled 'Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)' in the drive '/cdrom/' and press enter
```

I press enter and get:

```
Err http://security.ubuntu.com dapper-security/main libxfont1 1:1.0.0-0ubuntu3.1
  404 Not Found
Get:1 http://security.ubuntu.com dapper-security/main libxine-main1 1.1.1+ubuntu2-7.2 [2934kB]
Get:2 http://security.ubuntu.com dapper-security/main mozilla-thunderbird 1.5.0.5-0ubuntu0.6.06 [10.3MB]
Get:3 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-trident 1:1.0.1.2-0ubuntu1 [64.4kB]
Get:4 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-tseng 1:1.0.0.5-0ubuntu1 [32.5kB]
Get:5 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-v4l 1:0.0.1.5-0ubuntu1 [9730B]
Get:6 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-vesa 1:1.0.1.3-0ubuntu1 [14.4kB]
Get:7 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-vga 1:4.0.0.5-0ubuntu1 [12.7kB]
Get:8 http://us.archive.ubuntu.com dapper/main libdrm2 2.0-0ubuntu1 [14.2kB]
Get:9 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-via 1:0.1.33.2-0ubuntu4 [116kB]
Get:10 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-voodoo 1:1.0.0.5-0ubuntu1 [16.0kB]
Get:11 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-vmware 1:10.11.1.3-0ubuntu1 [19.2kB]
Get:12 http://us.archive.ubuntu.com dapper/main xserver-xorg-driver-all 7.0.0-0ubuntu45 [9116B]
Media change: please insert the disc labeled
 'Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)'
in the drive '/cdrom/' and press enter
```
It looks like it tries, but there's an odd space in the URL where /ubuntu/dists/ should be. What's going wrong?

---

### Post by Brunellus on 2006-09-19
comment out the lines about the CD in /etc/apt/sources.list

then

sudo apt-get update

then 

sudo aptitude install xubuntu-desktop

---

### Post by jonnythan on 2006-09-19
> **Brunellus said:**
> comment out the lines about the CD in /etc/apt/sources.list

then

sudo apt-get update

then 

sudo aptitude install xubuntu-desktop
Woohoo, thanks!

---

### Post by Brunellus on 2006-09-19
> **jonnythan said:**
> Woohoo, thanks!
w00t.

---

