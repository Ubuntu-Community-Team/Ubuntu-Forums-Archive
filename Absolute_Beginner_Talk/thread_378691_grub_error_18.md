---
title: "grub error 18?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2007-03-07
Hiya people,

I've got myself into a bit of a pickle with Ubuntu 5.10.

I'd like to re-download and install the latest Ubuntu, but I've made a bit of a spoon of an installation, leaving me unable to do so.

It went throught the installation of ver. 5.10 OK until the re-boot, upon which it's giving me an error.

I thought if anyone would know how to sort this out, it'd be someone here.

At the moment I'm stuck using a live disk, which is a life saver, if not ideal.

Anyone able to help a n00b in distress?

---

### Post by Drew555 on 2007-03-07
Seems I'm a bit of a pillock....

I've just done a search on grub error 18 and turned up 'Super grub Disk'.

Looks great, but since I'm a proper n00b, I can't actually download the file I need.

How do I download in Ubuntu live?

When i click on the file I want, I get an empty firefox window. No doubt it's summat simple, but apparently, so am I....

And wheres my floppy? I cant find it on the desktop....

I feel more issues coming..... Helllllllp meeeeeeeeeeeeeeeeeeeee...........

---

### Post by confused57 on 2007-03-07
I don't know if I can help you, I'm sure someone can...if you will, from the live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Drew555 on 2007-03-07
Thanks for the response!

Here's what I got:




Disk /dev/hda: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1001     8040501   83  Linux
/dev/hda2            1002        1048      377527+   5  Extended
/dev/hda5            1002        1048      377496   82  Linux swap / Solaris





Mean anything to you?

---

### Post by Drew555 on 2007-03-07
I'm desperately trying to download Super grub disk, but everytime I click on the filename, I get a blank window.

Please help, if the site is dead do you know of somewhere else i could download the one I need (to go on a floppy disk).

Thanks

This has the link I am talking about...


[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by confused57 on 2007-03-07
Maybe one of the "fixes" in this link will help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

You could try to reinstall grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

or possibly try reinstalling Ubuntu.

There is also the GAG bootloader which can be burned to a floppy:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
you "might" be able to do this from a live cd...

The Super Grub Disk download page is working for me, so it isn't down:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by Drew555 on 2007-03-08
I'm using firefox 5.0 and don't seem able to download from that site.

Any ideas?

When I click on the file I just get a blank window.

Getting desperate now....

---

### Post by Drew555 on 2007-03-08
I tried installing grub from the live cd like this:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

but still get the same error.

---

### Post by Drew555 on 2007-03-08
Going to try this and see what happens...

[http://www.ubuntuforums.org/showthread.php?t=368772&highlight=grub+error+18](http://www.ubuntuforums.org/showthread.php?t=368772&highlight=grub+error+18)

Will report back.

---

### Post by Drew555 on 2007-03-08
I reinstalled, using the advice in that thread, and have a fully functioning Ubuntu 5.10 install!

Won't bother updating though, probably just go straight to the latest Ubuntu.

Quick addition to that thread though.... it doesn't say whether to make the partitions logical or primary. I made them all primary and couldn't boot 'cos I didn't have an active partition.
Booted with a Win Me disk, ran fdisk, set partition 1 to active and was in business.

THANK GOD FOR LIVE DISKS AND UBUNTU FORUMS.

I will search better next time.

Thanks people.

---

