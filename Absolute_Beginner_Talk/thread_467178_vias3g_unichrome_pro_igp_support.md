---
title: "via/s3g unichrome pro igp support"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-07
I am new to Linux and have installed Ubuntu 6.10 then updated to 7.04.  I got my broadcom wireless working via ndiswrapper after going through several how-to's.  My biggest problem right now (at least in my naive Linux world!) is that I can't for the life of me figure out how to get the integrated via/s3g unichrome pro video working with anything other than the vesa driver.  My desktop area is "mis-sized" and I can't get access to more than 800x600 resolution.  I have tried to follow 2 separate how-to's for installing the unichrome drivers, including the unichrome.org drivers.  I never end up with a driver for "via" or "unichrome".  When I try to restart gdm with an updated xorg.conf file for "via" or "unichrome" it always comes up and tells me it can't find the device, and as a result no screen is found (I assume since I have no other device or screen defined in xorg.conf??).  Some of the time I have gotten as far as a via driver but it doesn't support my device (something to the effect of 3314 or some such thing).  This is the truncated output of an lspci:

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

After having looked through this forum, and many other web hits for ubuntu and via unichrome, I see that this is a very common problem among laptop users, even for non-via laptops.  I know this will sound dumb to some people, but there is a need for a very "dumbed-down" step-by-step of how to get this working.  I am an ex-systems programmer and systems administrator from large boxes, but LInux is a new animal to me and I am having a hard time trying to figure things out on my own using the how-to's and other web help.  Surely SOMEONE :phas gotten this working.  One of the ways I tried involved downloading the kernel source, Mesa and a bunch of other stuff, then aborting a make part way through (it said after 3 minutes, but on what platform is that timing based on?), etc..  The result of this was a complete failure for me and I know I now have a bunch of files "somewhere" in my tree that I don't use.;)  HELP!!!!????;)

Also, for all you experts out there, please don't get upset by this newbie comment, but "way back when" when we had Unix on a couple of machines at work (back in the very early 90's) it always seemed to be an "engineer's" OS, including very cryptic documentation.  I love the idea of open-source, especially having come from a proprietary operating system, and I love the strides that are being made to get away from something like Windows to a free OS.  I also understand the complexities of the multiple versions of Linux, the desktops, etc.  Now for the "but" ;) - we aren't close to that yet.  I have several friends who are just normal users - they don't know a darn thing technical about a computer at all, and they won't even try Linux because there is no "easy" way to just download a driver and install it, and there is not nearly enough software available.  PLEASE understand that I am not trying to be a Linux basher, but rather that for the common person - the deep base of Windows users - Linux is just not ready yet.  I hope it continues to work towards that.;)

As a personal note, does anyone have Family Tree Maker 10.0 working in Linux WINE??  That is the program I use the most, and so far I have not seen a Unix program that even comes close, not to mention the migration of thousands of people, photos, etc., to another program is a big task.  If I ever get to know Linux well enough, perhaps I can write something in Perl and MySql that would look similar and could perhaps be ported to other platforms (that's my longtime dream, anyway;)).

ANY help on my video driver would be so ever GREATLY appreciated not just by me, but by many others.  If it helps any, I have a Gateway MX3215 laptop with the default configuration except that I have 512mb of ddr2 (why, when it's a single slot, I'll never understand!!).  I know I can never expect to run beryl, etc., just as in Windows I could never expect to run the new desktop in Vista.  I'm not a big game player, I just want my resolution choices back and would LOVE to have FTM 10.0 running in Linux!!:)

---

### Post by gcos7 on 2007-06-07
Thanks so much for the responses - it really helps me and others to try to solve problems:(

---

### Post by NeoLithium on 2007-06-07
Hiya! 
I have the same video card as well in my laptop.  type:
```

sudo aptitude install xserver-xorg-video-unichrome

```

Though you have to make sure the repositories are enabled (See [http://www.ubuntuguide.org](http://www.ubuntuguide.org) ) if you don't have them yet :)

---

### Post by gcos7 on 2007-06-07
Thanks for the reply, but that is the one I tried that says my device is not supported - type 3344.

I have gotten higher resolution with the following link, but have no idea how to CHANGE resolution on the fly:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by dkaddict on 2007-06-17
I also use the Openchrome driver for my Via graphics. Everything works well and I can enable and use desktop effects in KDE and likewise in Gnome with xcompmgr. Doing so, however, renders my desktop environment useless. Any movement of scrollbars, windows, etc makes my fan scream and generally screws everything up.

In order to get my card working with Openchrome, I used the same how2 that you linked ([https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)). In order to change my screen resolution after compiling the Openchrome driver and amending xorg.conf, I had to enter>>

sudo dpkg-reconfigure -phigh xserver-xorg

and check the relevant values (arrows spacebar)

Again, X performs well with Openchrome but Beryl, Compiz, etc are out of my cards league. It doesn't look as though that will ever change so only a new laptop with an, for eg, Invidia card will solve the Beryl Compiz issue. It is a shame, but that's how it is. 

peace

dk

---

### Post by xhizors on 2007-07-31
you can change your resolutions and add more choices by running:

```
sudo dpkg-reconfigure xserver-xorg
```

select VESA if that's what you're using... run through it
at the end it asks you what resolutions will be avaliable...
press the spacebar to select the ones you'd like then hit enter...

then reboot xserver

---

