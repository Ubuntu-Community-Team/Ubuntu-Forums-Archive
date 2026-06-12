---
title: "old mac- which ubuntu version and where to get it?"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by denphi03 on 2009-04-24
hey everybody!

i have an old (2003-4) ibook 800 mhz w/ 384 mb RAM. yeah, its old and weak. BUT

its got mac os x 10.2 or something i dont like it and i love ubuntu. i want to fresh install ubuntu on the entire drive. no partitions

im also pretty sure that its powerpc

...so which version should i use? the computer is old so i assume i should use an older version of ubuntu, but i have no idea which version i shuold use or where to get it

thanks in advance for the help

---

### Post by bug67 on 2009-04-24
At the very top of this forum, there's a sticky titled, "Where to download Ubuntu for PowerPC and other frequently asked questions?"

Direct linky:

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

> **denphi03 said:**
> "...im also pretty sure that its powerpc..."

To make sure it's a PPC, boot into OS X and click the little apple in the upper left of the screen and select, "About this Mac."  If it's a G3 or later (probably is) it's a PowerPC.

The above link will answer most of your questions.

---

### Post by denphi03 on 2009-04-24
> **bug67 said:**
> Did you see the sticky at the very top of this forum?  The one titled, "Where to download Ubuntu for PowerPC and other frequently asked questions?"

Direct linky:

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

yes.

that doesn't answer my question.

which version do i need for my old computer?

---

### Post by bug67 on 2009-04-24
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by denphi03 on 2009-04-24
i think this is the one i was looking for. thanks

---

### Post by mkvnmtr on 2009-04-24
I would install 8.04 on that machine. I say 8.04 because I know it is an easy install and 8.10 had some problems that I never faced, I just upgraded. After I here about a few 9.04 installs I may recommend it. My ram usage has been about the same from 6.06 to 8.10 so I don't see a reason to use an older distro. I would add at least a 256Mb stick of ram to the machine. In most parts of the world it is not to expensive.

---

### Post by stream303 on 2009-04-25
And since you want to dedicate the entire machine, don't sweat the partitioning.  Unless you have specific needs, when it comes to the guided-partitioning process, just let it "use the whole disk" when prompted, and it should take care of everything for you.

---

### Post by denphi03 on 2009-04-27
im having some issues with the install. it's not seeing the disc as 'bootable'

im not a mac guy, so i dont know all the tricks to getting it to do what i want

i tried going into startup disk manager, but its not seeing the ubuntu disk as an option.

i tried 7.04, i think if theres no system requirement issue i might try 8.04 or 8.10. im using 8.10 on my laptop currently and i love it

also if i can get this thing running the way i want i plan on maxing the ram on this machine (640mb i think)

any ideas of how i can get this animal to boot properly so i can install?

---

### Post by tiresia on 2009-04-27
I don't any reason, why you shouldn't try also jaunty 9.04
If you like it, xubuntu is a bit lighter than ubuntu or kubuntu (i mean xfce is lighter that gnome or kde)
To download jaunty via http
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)
or with a bittorrent client
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
Be patient, because servers are still a bit overloaded (may be use bittorrent if you know how it works) 

You can download the alternate installer cd (only text), or even try a LiveCD.

If you are burning the cd in macosx, be sure to use the apple disk utility (better at low speed) choosing the .iso file you downloaded.
You don't need to use the apple startup disk - just insert the cd and press the C-key at bootup.

---

### Post by denphi03 on 2009-04-27
> **tiresia said:**
> I don't any reason, why you shouldn't try also jaunty 9.04
If you like it, xubuntu is a bit lighter than ubuntu or kubuntu (i mean xfce is lighter that gnome or kde)
To download jaunty via http
[http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)
[http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/jaunty/release/)
or with a bittorrent client
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
Be patient, because servers are still a bit overloaded (may be use bittorrent if you know how it works) 

You can download the alternate installer cd (only text), or even try a LiveCD.

If you are burning the cd in macosx, be sure to use the apple disk utility (better at low speed) choosing the .iso file you downloaded.
You don't need to use the apple startup disk - just insert the cd and press the C-key at bootup.

burning the disk with either xp or ubuntu 8.10

c-key trick isnt working

startup manager does not recognize

i suspect the firmware is locked. gonna try the 'ol zap the ram trick tonight if i have time

---

### Post by stream303 on 2009-04-27
Don't forget to burn the iso cd as an iso, and at a very low speed, something that the mac can handle, preferably a CD-R.

You may also want to try burning the "alternate" image, which is a text-only installer (full gui afterwards) in case the live-cd doesn't properly detect the graphics card.  At least with the alternate, you'll get the data on the disk whereby you can at least get to the cli and more easily change your /etc/X11/xorg.conf file if you need to manually configure the ATI graphics card.  Sometimes the installers, especially with ATI graphics, don't get it right out of the box due to the apple hardware quirks.

---

