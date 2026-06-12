---
title: "Using wireless network"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Zarfoz on 2007-02-06
Hi!
I installed Ubuntu today, so Im totaly new to all of this.

Id like to know how to connect to my wireless network. I have a Ralink network card (that works fine with windows)..

So, what should I do to connect to internet?

Thanks

---

### Post by tocleora on 2007-02-06
In System > Administration > Networking, you should see the wireless card in there.  Select it, hit "properties' and you should be able to set it up just like you do in windows.  It's been a while so unfortunately I can't be of further assistance (like with WEP or WPA) but maybe that'll get you a little further. ;)

---

### Post by Zarfoz on 2007-02-06
The problem is that my LAN card isnt in that list.
How to install drivers or something like that on Ubuntu when the card only came with drivers for windows?

Thanks for helping me out

---

### Post by Zarfoz on 2007-02-06
My lan card is: CNet Wireless-G CWP-854

---

### Post by Zarfoz on 2007-02-06
Bump.. :(

---

### Post by tocleora on 2007-02-06
Well, from my experiences in Windows I immediately think "detect new hardware" if that doesn't work "install drivers"... so, doing a search for "detect new hardware", this is the only thing I found that may be of relevance:

[http://www.ubuntuforums.org/showthread.php?t=58652](http://www.ubuntuforums.org/showthread.php?t=58652)

and maybe this although it's older:

[http://www.linuxquestions.org/questions/showthread.php?t=399951](http://www.linuxquestions.org/questions/showthread.php?t=399951)

If that doesn't work, then you should probably visit the manufacturer's web site and see if they have a linux/ubuntu driver for it.  

Another thread you may find of value:

[http://www.ubuntuforums.org/showthread.php?t=293443&highlight=wireless+network+card](http://www.ubuntuforums.org/showthread.php?t=293443&highlight=wireless+network+card)

Hope that helps move you forward...

---

### Post by ^rooker on 2007-02-06
If I'm not mistaken, Linux "detects" new hardware automagically - at least if the right module is loaded, but that's something "discover" is taking care of in Debian/Ubuntu (for stuff that ain't compiled directly into the kernel).

For your network card I guess you'll have to use ndiswrapper - at least I see your card on their list:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

ndiswrapper is a way of "wrapping" linux-wifi-driver-api around the original windows driver. This reduces some functionality of this card under linux, but usually works (see list).


Here's [how I got a Marvell WiFi card working]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=415&highlight=wireless") with ndiswrapper.

---

### Post by Zarfoz on 2007-02-07
It asks me for password when i type sudo ndiswrapper blablabla.inf.. What password am I supposed to type?

Thanks

---

### Post by ^rooker on 2007-02-07
sudo asks you for *your* password. :)

Maybe you should do a little reading about "sudo", because it will become a beloved friend - seen very often. :)

---

### Post by tocleora on 2007-02-07
Your superuser/root password.  sudo = "superuser do".  If you don't know or don't remember setting one up, try your regular password.

---

### Post by Zarfoz on 2007-02-07
The password I use when i log on doesnt work. That´s the problem.

---

### Post by username132 on 2007-02-07
Edit; started my own thread (on similar issue of wireless network card setup).

---

### Post by Zarfoz on 2007-02-08
Bump

---

### Post by tocleora on 2007-02-08
It's the password of the 1st user account you set up, if you aren't using the 1st user account set up then try that password.  If you are, then maybe this article will help:

[http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html](http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html)

---

