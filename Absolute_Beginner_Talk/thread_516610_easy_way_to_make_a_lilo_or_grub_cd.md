---
title: "easy way to make a lilo or grub cd?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by garyflynn on 2007-08-03
I want to by default, boot directly into XP, without any menu, using the MS MBR settings, whatever they are.

But I want to burn a cd, that if it is in the drive at boot time, will give me a menu that will let me boot from the XP partition on the hard drive, a Vista partition or my new Ubuntu 7.04 partition.

How would I get a grub or lilo menu onto a bootable iso, then burn that to a cd?

If there is a gui way to do it, that is much preferred.

Thanks

---

### Post by startherepodcast on 2007-08-03
Hi,

You could try isolinux, [http://syslinux.zytor.com/index.php]("http://syslinux.zytor.com/index.php")

I think this is what the live ubuntu live cd menu is made with, (someone correct me if i'm wrong)

Good Luck

Adsized

---

### Post by startherepodcast on 2007-08-03
You May Also Want to Check Out: [http://ubuntuforums.org/showthread.php?t=21756]("http://ubuntuforums.org/showthread.php?t=21756")

---

### Post by garyflynn on 2007-08-04
I guess one of the links below will yield a grub boot cd I'm not at my linux machine right now.

[http://www.linuxquestions.org/questions/showthread.php?p=729330#post729330](http://www.linuxquestions.org/questions/showthread.php?p=729330#post729330)

[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

****

I wish there was a gui way to do it, I've seen a gui that steps the user through creating a grub bootup menu with entries of OSs that are detected on the hard drive and even deciding where to store it, the mbr, the partition or a floppy.

I can't find that in ubuntu though. Can anyone help?

---

### Post by garyflynn on 2007-08-04
To continue answering my own question, in a place that will be easy for me to find later:

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

grubed seems to be a gui that will create and edit the necessary grub files before burning to cd.

[http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD](http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD)

This is a set of command line instructions that do exactly what I am asking.

---

### Post by MQMike on 2007-08-04
Yes, and Herman at bigpond also tells you all about Super Grub Disk, which will do this for you -- you download and burn iso etc., all as usual.
Or, use other stuff Herman tells you about there at his site.
It's the classic reference for this subject.
(see garyflynn's second ref.)

---

