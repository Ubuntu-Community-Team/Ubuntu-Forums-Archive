---
title: "Question about the Ubuntu bootloader"
date: 2007-10-31
forum: Apple Intel Users
---

### Post by CaptSaltyJack on 2007-10-31
When I installed Gutsy on my Mac Pro, it asks if I want to install the bootloader on hd0.  I said no, because I wasn't sure if it would mess up my Tiger partition.  But then I held down Option while booting the Mac, and chose the Ubuntu partition, and it didn't boot..

So, if I say yes, install the bootloader, how will that work?  I assume I still have to hold Option during boot, then choose the Ubuntu partition, and then I'll see the Ubuntu bootloader screen?

Also, I noticed the Mac calls the Ubuntu partition "Windows" on the Mac boot up screen.  How can I rename that?

Thanks!

---

### Post by tubasoldier on 2007-10-31
I'm not sure how to change the "Windows" designation by your mac. 

However, you are on the right track. To boot Ubuntu the way you have described, you need to install grub (linux bootloader) to your Ubuntu partition. I assume this would be hda(0,1) or something like that. Verify this before you start telling grub to install to that partition.
Anyways, there is an advanced option during the installation. However, I can not remember what window it is in. It is also possible to install it without actually re-installing Ubuntu.

NOTE: hard drives are designated in this manner:
                 hda = first hard drive.
                 hdb = second hard drive.
                 hd0 = Master Boot Record
                 hda(0,0) = first primary partition
                 hda(0,1) = second partition
          It moves up incrementally like that.

---

### Post by cyberdork33 on 2007-10-31
> **CaptSaltyJack said:**
> When I installed Gutsy on my Mac Pro, it asks if I want to install the bootloader on hd0.  I said no, because I wasn't sure if it would mess up my Tiger partition.  But then I held down Option while booting the Mac, and chose the Ubuntu partition, and it didn't boot..

So, if I say yes, install the bootloader, how will that work?  I assume I still have to hold Option during boot, then choose the Ubuntu partition, and then I'll see the Ubuntu bootloader screen?

Also, I noticed the Mac calls the Ubuntu partition "Windows" on the Mac boot up screen.  How can I rename that?

Thanks!
It is ok to install to the default location. If you are also booting windows, you will want to install to the Ubuntu partition rather than the MBR:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

Also, you might checkout [rEFIt]("http://refit.sourceforge.net/") as an alternative to holding ALT. It will recognize the partitions correctly too.

---

