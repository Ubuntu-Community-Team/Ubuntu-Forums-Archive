---
title: "[SOLVED] Adding a Windows XP boot. :-( I was so close to never having to use windows"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by bazzard on 2007-11-30
Hi

Ok, so i've been using Ubuntu for about a month now. And I love it. Does everything I want with the bonus of lots of eye candy from Compiz. 

There's just 3 things that I can't do in LInux though.

1. Play PKR

2. Use nokia PC suite

3. iTunes and iPod syncing. (just bought one today and want to be ready and be able to do what it's supposed to on the PC with iTunes without having any problems when it arrives)

I installed virtual box with an XP install. Worked great, I thought I had found my answer. But sadly trying to get the N95 and pc suite to talk to eachother didn't work. PKR won't run because of a D3D error and I know that it's near impossible to sync an ipod properly with itunes on virtual box from reading the forums.

So that's it, I have to install windows properly on a new partition. However, the n00b that I am, I have never done this before, so I need some help to explain to me first how to create a partition to install XP on and secondly how to make sure I am able to run both OS's still once I've installed it. I've read something about having to reinstall the grub or something. greek to me.

A step-by-step guide would be much appreciated.

cheers

---

### Post by Xylograph on 2007-11-30
I was under the impression that GTKPod was fine for syncing with iPods in Linux. Id give it a shot.


However, I cannot help with the rest unfortunately.

Good luck!

~Xylo'

---

### Post by stchman on 2007-11-30
> **bazzard said:**
> Hi

Ok, so i've been using Ubuntu for about a month now. And I love it. Does everything I want with the bonus of lots of eye candy from Compiz. 

There's just 3 things that I can't do in LInux though.

1. Play PKR

2. Use nokia PC suite

3. iTunes and iPod syncing. (just bought one today and want to be ready and be able to do what it's supposed to on the PC with iTunes without having any problems when it arrives)

I installed virtual box with an XP install. Worked great, I thought I had found my answer. But sadly trying to get the N95 and pc suite to talk to eachother didn't work. PKR won't run because of a D3D error and I know that it's near impossible to sync an ipod properly with itunes on virtual box from reading the forums.

So that's it, I have to install windows properly on a new partition. However, the n00b that I am, I have never done this before, so I need some help to explain to me first how to create a partition to install XP on and secondly how to make sure I am able to run both OS's still once I've installed it. I've read something about having to reinstall the grub or something. greek to me.

A step-by-step guide would be much appreciated.

cheers

PKR?  Is that the online poker playing thing?  Try running it in WINE.

Nokia stuff - try WINE again.

Ipod - Use either gtkpod or amarok

If you already have Ubuntu installed XP will overwrite GRUB so you have to reinstall GRUB.

---

### Post by bazzard on 2007-11-30
PKR doesn't work under wine, i got very close but it crashes after a few minutes, i got further than anyone else though it seems. see this thread. [http://ubuntuforums.org/showthread.php?t=410862](http://ubuntuforums.org/showthread.php?t=410862)

PC suite also doesn't work in wine. I will try out gtkpod, but as it is my first ipod I'd really like to use itunes and have a proper play around with it the conventional way with itunes.

So, i still need help on getting a windows partition up and running please someone.

---

### Post by Dark_X on 2007-11-30
This should help:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by forestpixie on 2007-11-30
you'll need to make a partition for it to live in, I use gparted as a [livecd]("http://gparted-livecd.tuxfamily.org/download.php") to do my partitioning. You'll have to do a resize of an existing one, format it to ntfs then when you restart with the xp disc you should have the partition ready to go.

You're right, once you've installed it XP will overwrite the boot with it's stuff. These pages should be able to get you on the way with redoing you're grub, but I use [supergrub]("http://supergrub.forjamari.linex.org/?section=download") myself - yet another livecd :)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It might need the win partition at the beginning of the drive - not sure about that - gparted will let you move partitions as well.


Before you do anything with your partitions - make sure you've got a readable backup for justin

---

### Post by bazzard on 2007-11-30
> **Dark_X said:**
> This should help:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

FANTASTIC! Exactly what I was looking for. I will give it a go and see how I get on.

I don't think we're that far from not needing Windows. Nearly there, it's just those little things here and there that need the same functionality that you can only get by using the windows based applications.

---

