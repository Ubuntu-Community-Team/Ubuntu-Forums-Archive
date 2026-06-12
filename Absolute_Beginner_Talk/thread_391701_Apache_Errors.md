---
title: "Apache Errors"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-23
Everytime I use the terminial or I use synamptic, etc it gives me an error about apache:
```
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How do I fix it?

---

### Post by ProjectWhat on 2007-03-23
/usr/bin/dpkg doesn't exist. so what do I need to put there to fix it. I tried to unintall apache but got errors doing that too.

```
ben@ben-ubuntu:~$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java xserver-xorg-video-rendition xserver-xorg-input-evdev
  xserver-xorg-video-newport xserver-xorg-video-s3virge xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-glint
  xserver-xorg-video-fbdev xserver-xorg-input-wacom xserver-xorg-video-v4l
  xserver-xorg-video-mga xserver-xorg-input-mouse xserver-xorg-video-nsc
  liblog4j1.2-java xserver-xorg-video-vesa xserver-xorg-video-siliconmotion
  xserver-xorg-video-tga xserver-xorg-video-sis libswt3.2-gtk-java
  xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-s3
  libseda-java xserver-xorg-video-nv libcommons-cli-java xserver-xorg-core
  libgtk-jni xserver-xorg-video-tseng apache2 xserver-xorg-video-savage
  libcairo-java xserver-xorg-input-all libbcprov-java
  xserver-xorg-input-elographics xserver-xorg-video-vmware
  xserver-xorg-input-kbd localechooser-data libglib-java
  xserver-xorg-video-i128 xserver-xorg-video-neomagic xserver-xorg-video-chips
  xserver-xorg-video-voodoo xserver-xorg-video-i740 xserver-xorg-video-i810
  libgtk-java xserver-xorg-video-cyrix xserver-xorg-video-dummy
  libswt3.2-gtk-jni xserver-xorg-input-synaptics xserver-xorg-video-sisusb
  xserver-xorg-video-imstt xserver-xorg-video-cirrus
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147190 files and directories currently installed.)
Removing apache2 ...
Setting up apache (1.3.34-4ubuntu1) ...
 * Configuration syntax error detected, not starting/reloading...               
Syntax error on line 1 of /etc/apache/conf.d/vhost.conf.gz:
Invalid command '&zCvhost.conf', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                         [fail]
invoke-rc.d: initscript apache, action "start" failed.
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@ben-ubuntu:~$ 
```

---

### Post by DoorGunner on 2007-03-23
try 
sudo update-rc.d apache2
sudo update-rc.d apache

it looks like the remove process forgot to update your services

---

### Post by ProjectWhat on 2007-03-23
> **DoorGunner said:**
> try 
sudo update-rc.d apache2
sudo update-rc.d apache

it looks like the remove process forgot to update your services

when I do that It does this:
```
ben@ben-ubuntu:~$ sudo update-rc.d apache2
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
ben@ben-ubuntu:~$ sudo update-rc.d apache
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
ben@ben-ubuntu:~$ 

```

---

### Post by DoorGunner on 2007-03-23
It just gave an error for the usage. However, they have clues as to what to do.

if you man update-rc.d 
-n indicates do nothing
-f indicates force

Try this than 

sudo update-rc.d -f apache2 remove
sudo update-rc.d -f apache remove

that should remove the scripts

---

