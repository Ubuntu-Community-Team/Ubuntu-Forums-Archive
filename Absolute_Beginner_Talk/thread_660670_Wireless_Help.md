---
title: "Wireless Help"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-01-07
I have Ubuntu 7.10 Gutsy Gibbon and I have a Toshiba Satellite A215-S7437. How to I get wireless to work on the computer? Do I need to give more info on my computer?

---

### Post by HermanAB on 2008-01-07
Basically, what you need to do is go to ndiswrapper.sourceforge.net and start reading.

Cheers,

Herman

---

### Post by manmohanpv on 2008-01-07
Install wicd

sudo apt-get install wicd

reboot, wicd takes a little time to show up the dialog, choose ur wireless access point and provide the password.

also look at the /etc/network/interfaces file and try to edit it like this if doesnt connect

iface eth1 inet dhcp
wireless-essid urwirelessaccesspointname
wireless-key urkey

auto eth1

its working fine in my system...network manager find it tough to connect..thats why try wicd...

-thanks
manmohan

---

### Post by supertails on 2008-01-07
I have read the site and their are many versions so I'm guessing I download to most current version on there.  I download 1.51 but is there anything else?

---

### Post by supertails on 2008-01-07
Can you install software on Ubuntu just as easy as with Windows?

---

### Post by corevette on 2008-01-07
it's wayyy easier in ubuntu to install software...everything is automatically updated
you won't go back

---

### Post by gunbladeiv on 2008-01-07
depends on the file you download.  If it's .deb then you can install it by double-click the file.deb.
but if you download .tar.gz/tar.gz.bz2 type of files you need to compile it.
it's not hard to install/compile.  Just need to know the steps.

---

### Post by stalkingwolf on 2008-01-07
OR you can use synaptic package manager ( system> administration> synaptic package manager) or
Applications> add/remove ,  select the software desired , click install.

dont get much easier than that.:guitar:

---

### Post by supertails on 2008-01-07
Thank you guys for the help. I'm guessing exe files won't. I'm indifferent to games though does it good games though. I'm okay if it doesn't because I'm pretty indifferent to games.

---

