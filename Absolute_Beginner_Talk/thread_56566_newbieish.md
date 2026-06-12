---
title: "newbieish"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by applejack on 2005-08-13
Hi,

I have decided to install linux on my new second hard drive and I am going with Ubuntu because I heard good things about it. I am not a compltete novice to linux I have installed a few differant versions of it throgutout the years. I havent tried it in about four  or five years so I'm sure things have changed alot.

Couple of basic questions. Wheneever I reinstall windows on my comp the first thing I do is install zone alarm before I setup my net connection. Do I have  to install a firewall on Linux, or configure any special security settings afetr I install?  I remeber in the old days of Linux all I had to do was edit host.allow and host.deny files. Is that still the case?

Will it automaticly detect my DSL internet connection? My internet settings are all stored on my router/modem/little black box thingy anyway so I just need to connect to that. The Slax live cd detects my connection and lets me browse the web without me having to do anything so I assume it will be okay.

This is probably a quetion for the hardware forum but since I am here asking  questions anyway I hope you dont mind. Will the X windows system (if it's still called that) detect my Radeon 9600 Pro or will I have to download addtional drivers?

cheers for your help.

---

### Post by heimo on 2005-08-13
Hi! Welcome to world of Ubuntu.

In default install Ubuntu does not have any outbound listening services running and firewall is not absolutely neccessary. You can install a nice frontend firestarter to make firewall rules. Most important security task is to upgrade packages when new versions get released (these are mostly security patches on Hoary which is otherwise in very stable state). No you don't need to edit hosts.allow/deny.

If you're using DHCP (which it sounds you do), network is probably automaticly configured and "just works". Easy. Very easy compared to the days when there was no autodetection and you had to manually load modules (and many times choose correct IRQ/IO settings...)

Your card should work fine with vesa (not recommended), ati and fglrx (proprietary, has to be installed after install) drivers. Ati is definitely not the best card for Linux, but should be ok.

fglrx driver installation:
[http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

Hopefully this answers most of your questions, feel free to make more questions and ask for help on these forums if you encounter any problems during or after install. :)

---

### Post by PeP on 2005-08-13
[QUOTE=applejack]Hi,

Couple of basic questions. Wheneever I reinstall windows on my comp the first thing I do is install zone alarm before I setup my net connection. Do I have to install a firewall on Linux,
[/QUOTE]

you do not need to do it first, because no port should be open after the install, but don't leave it like this for days if you plan to install stuffs .

```
nmap localhost
``` can tell you wich port is open if an application opens one and you don't see a remote use for it, then firewall it.

a good policy should be to install the firewall as soon as your installation is complete (the full install may require the network and you can safely install firestarter from synapitc)


> 
 or configure any special security settings afetr I install? I remeber in the old days of Linux all I had to do was edit host.allow and host.deny files. Is that still the case?


if you know what you want from host.allow, host.deny, it is a good thing.
Anyway you won't take much risks until you open a port.


> 
Will it automaticly detect my DSL internet connection? My internet settings are all stored on my router/modem/little black box thingy anyway so I just need to connect to that. The Slax live cd detects my connection and lets me browse the web without me having to do anything so I assume it will be okay.


If slax detects it and ubuntu doesn't hum what a shame ...
I assume you are connected to your modem with ethernet (network card, NOT usb), then you will have no trouble.


> 
This is probably a quetion for the hardware forum but since I am here asking questions anyway I hope you dont mind. Will the X windows system (if it's still called that) detect my Radeon 9600 Pro or will I have to download addtional drivers?

cheers for your help.

there are free oss drivers for ati cards without 3d accel, ubuntu will provide you theses and everything  will work apart from 3d accel :-p

If you enable extra repositories (check links from the post in my sig) you will be able to install linux-restricted-module-2.6.10-5-386 (replace the figures by the result of uname -r) 

this will install the official non-free driver from ati.

you might have to search a bit this forum or the web to configure it.

---

### Post by nic2 on 2005-08-13
For guidance on security related matters checkout the user documentation on the Ubuntu Wiki, more specifically point 4.1 Security.  The link as follows:

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by applejack on 2005-08-13
Thanks guys 

The netwrok stuff sounds like it will be fine.  As for the video card as long as I get a GUI at first I'm happy. I will probably be using only 2d apps anyway, if I need to use 3d I can always look into the other drivers  later.

Will post more quetions if I think of them.

---

