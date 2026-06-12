---
title: "Can't conncet to Internet"
date: 2007-02-02
forum: Apple PPC Users
---

### Post by don skoog on 2007-02-02
Hi Guys,

I've been trying for two weeks to connect my newly installed Ubuntu 6.06.1 to the internet.

It's in a Thinkpad 600.
The Wireless card is a Linksys Wireless-G
I'm trying to connect to my Airport Base Station

System>Administration>Networking lists: Wireless Connection and Modem Connection but does not show my wireless card by name. I have typed my setting in many times with no results.

So I'm assuming it doesn't recognize my card.

The computer is partitioned and the Windows system connects to my base station with no problem so I thought I try to use it as you guys outlined in [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

This creates new problems:

I can't check to see if it has a broadcom chipset because I don't know how to type in the upright line in  <lspci | grep Broadcom\ Corporation> (I'm writing from my Mac and just copied the command here).

I can't install the bcm43xx-cutter (which sitting on my desktop) because<sudo apt-get install bcm43xx-fwcutter> returns with "no such file"

Synaptic Package Manager (after I searched and found bcm43xx-cutter) shows no package to install. Reload tells me "Could not download all Repository indexes and lists four repositories ([http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:Temporary](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:Temporary) failure resolving 'us.archive.ubuntu.com', for example).

I'm stumped. Is there another approach or should I just buy a Linux supported wireless card? Can you recommend a wireless that will work without all this hassle?

Help!

Don

---

### Post by ssam on 2007-02-03
hi

if you are on a thnk pad, then the powerpc forum is not the right place to post in. the networking forum will probably get you a better answer.

the | should be on you keyboard somewhere. sometimes it is drawn with a gap in the middle see [http://en.wikipedia.org/wiki/Vertical_bar](http://en.wikipedia.org/wiki/Vertical_bar) . if your keyboard down not have it find it in systems -> accessories -> character map, and copy and paste it.

or if you just run
```
lspci
```
on its own it will give you a full list of your hardware. (the grep bit is a filter).

also try the command
```
iwconfig
```
that might show if you have a working wireless card

---

