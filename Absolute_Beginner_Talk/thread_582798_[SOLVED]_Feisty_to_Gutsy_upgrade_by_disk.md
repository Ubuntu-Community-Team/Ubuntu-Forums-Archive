---
title: "[SOLVED] Feisty to Gutsy upgrade by disk?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-20
Due to a fault I describe in this post - [http://ubuntuforums.org/showthread.php?t=579942](http://ubuntuforums.org/showthread.php?t=579942) - my Update Manager isn't working.

Is there a way of upgrading from disk instead which will preserve my current settings, programs, etc, or does a disk install always consist of a clean install?

Assuming the latter, I am running dual boot, and - having installed Ubuntu so long ago - got distinctly nervous when I got to the stage where it asks how to partition disks - how do I make it use the settings I already have?

Thanks!

---

### Post by forestpixie on 2007-10-20
If you get a copy of the alternate install you can upgrade with that - see [here,]("https://help.ubuntu.com/community/GutsyUpgrades") in particular the end

---

### Post by qprfact on 2007-10-20
Thanks! I will give it a try!

---

### Post by qprfact on 2007-10-20
Well, I downloaded it and booted up, but there was no option on the menu for upgrade! Is it described in some other way? Everything seemed to be pointing towards a clean install (albeit with different options to the desktop CD)

I tried the command too, but got no joy with either! (I can't remember message exactly, but it was something like command not recognised)

---

### Post by qprfact on 2007-10-20
Right, just booted in via disk again. These are the options:

Install Text Mode
OEM Install
Install Command line
Check CD
Rescue broken system
Memory test
Boot from first hard drive

Alt & F2 does nothing - brings up no screen, or changes current one at all.

So I thought Rescue Broken System might be it, but before long it's talking about partitioning of sda1, etc, which doesn't sound like an upgrade to me!

---

### Post by forestpixie on 2007-10-21
you need to be running in Ubuntu - not booting to the disc I think

then

> If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesu "sh /cdrom/cdromupgrade"


I assume that if you boot with the disc it's going to think you want to install

---

### Post by qprfact on 2007-10-21
You're right.

Unfortunately, upgrade wouldn't work, so I had to go for clean install, Which, despite the fact that I don't have data on my Linux partition, still took ages to get all my programs and settings back as they were (oh for a reliable backup settings option!)

I now have another issue with display, but will make that into a new thread!

Thanks for your help on this - much appreciated

---

### Post by forestpixie on 2007-10-21
not a problem - can you mark thread solved if you feel it is :)

---

