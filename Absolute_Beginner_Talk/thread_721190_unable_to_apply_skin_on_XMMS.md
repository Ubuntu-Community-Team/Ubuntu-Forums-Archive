---
title: "unable to apply skin on XMMS"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2008-03-11
Hi
I want to install this [http://www.gnome-look.org/content/show.php?content=41102&forumpage=2](http://www.gnome-look.org/content/show.php?content=41102&forumpage=2) skin on my ubuntu 7.10 with xmms 1.2.10 
So i downloaded VU-meter plugin Version >= 0.9.2 but when i try to compile it it gives me following error :
```

checking for GLIB - version >= 1.2.10... yes
checking for xmms-config... no
checking for XMMS - version >= 1.2.9... no
*** The xmms-config script installed by XMMS could not be found.
*** If XMMS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XMMS_CONFIG environment variable to the
*** full path to xmms-config.
configure: error: *** XMMS >= 1.2.9 not installed - please install first ***
saurabh@ubuntu:~/Desktop/vumeter-0.9.2$ 

```
plz tell me how to fix this problem I have xmms 1.2.10 on my ubuntu 7.10 i m unable to find xmms 1.2.9 on internet :( 
help me to install this skin plz

---

### Post by k33bz on 2008-03-11
should be able to go to the synaptic mangager and go to the currently installed XMMS, and install a previous version.

---

### Post by martinx73 on 2008-03-31
Ubuntu 7.10 - 25 Marzo 2008

install with synaptic
xmms
xmms-dev
gcc
gcc-4.2
gawk
libgdk-pixbuf-dev
libglib1.2-dev

download the plugin from
[http://vumeterplugin.sourceforge.net/download.php](http://vumeterplugin.sourceforge.net/download.php)

decompress
move to folder decompress

with a terminal
sudo ./configure
sudo make
sudo make install
sudo mkdir /usr/share/xmms/VU_Meter_skins
sudo cp -R skins/* /usr/share/xmms/VU_Meter_skins

in xmms
press Control+v
select plugin
click in configure
select skin

PD 
sorry, my english is very basic

---

### Post by saurabh kakkar on 2008-04-01
Thanks buddy installed it :) thanks for the Help nd PM

---

