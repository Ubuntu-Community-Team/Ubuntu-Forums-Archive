---
title: "Delete Ubuntu Partition from Mac"
date: 2013-11-24
forum: Apple Hardware Users
---

### Post by mcmacker4 on 2013-11-24
I would like to uninstall Ubuntu from my mac because I have some audio issues and I couldn't solve them so I never use Ubuntu.

My question is a very simple one: Can I use Mac's Disk Utility to delete the partitions? Or do I have to use a Ubuntu Bootable USB to delete the partitions using GParted?
I ask this because a long time ago I deleted the USB stick and now I can't manage to create a new one. The computer simply doesn't detect it...

Thank you in advance :)

---

### Post by bapoumba on 2013-11-24
Moved to Apple Users.

When and how did you install Ubuntu ?

---

### Post by mcmacker4 on 2013-11-24
I installed in the beggining of this summer. I created a 50gb partition in my drive and installed Ubuntu 12.04 using a usb stick.

---

### Post by bapoumba on 2013-11-24
[http://ubuntuforums.org/showthread.php?t=1705806](http://ubuntuforums.org/showthread.php?t=1705806)

Even though I do own Macs, they are work ones and I never installed ubuntu on them. I looked around and found the above thread (among many) that may have useful info. Basically, they removed the partitions with gparted and reclaimed the free space with Disk Utility.
If on Lion or up, you can get to Disk Utility holding Command-R while booting (hold it long enough).

---

### Post by mcmacker4 on 2013-11-25
I apreciate your research but the problem I have is that I can't manage to create the usb stick any more and that is why I can't use gparted, so my question is: can I use Mac's Disk Utility to delete those Ubuntu partitions?

---

### Post by bapoumba on 2013-11-25
The partitions are formatted in ext4, so unless you use some extra application, I do not think so. I've always done it the other way around, format usb sticks in HFS+ from ubuntu or MacOS to be used by both.
Can you use a CD or DVD ?

---

### Post by Lars Noodén on 2013-11-26
I tried on a spare machine (10.6).  On the running OS X system, the EXT4 partitions could be reformatted but it had trouble with the swap and boot partition.  However, booting the Disk Utility on the10.7 install DVD, I was able to remove the Ubuntu partitions and resize the OS X partition to use the recovered space.

---

### Post by mcmacker4 on 2013-11-26
So I managed to make a Ubuntu Live DVD and I deleted both the ext4 and the linux-swap partitions. Now the problem is that ubuntu is still appearing in rEFIt.
Any ideas why this is happening?

I would also like to mention that there was another partition of unknown format and was only some Kb big. Does that have anything to do with the problem mentioned previously?

Thank you for your support :)

---

### Post by Lars Noodén on 2013-11-26
You'll have to remove rEFIt using OS X.

[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

If you have the OS X installation media you can resize the OS X partition to use up the freed space, too.

---

### Post by mcmacker4 on 2013-11-26
> **Lars Noodén said:**
> You'll have to remove rEFIt using OS X.

[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

If you have the OS X installation media you can resize the OS X partition to use up the freed space, too.

Yeah but I would like to install Windows now so I'll be needing rEFIt later. Is there any other way to remove Ubuntu from rEFIt?

---

### Post by Lars Noodén on 2013-11-26
It would be much safer to use that other system only inside a virtual machine like VirtualBox.  That way when you need it, you can not only start it nearly instantly, but also only ever start up from a clean snapshot.  Using snapshots limits the amount of security exploits and cruft.

---

