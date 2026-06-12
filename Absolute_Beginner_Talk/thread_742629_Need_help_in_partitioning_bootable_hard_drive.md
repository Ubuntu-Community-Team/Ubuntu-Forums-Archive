---
title: "Need help in partitioning bootable hard drive"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by binsiram on 2008-04-01
I have not partitioned my 250 gig hard disk intially when I installed ubuntu (7.10) 
Now I want to install vista, but for that I need to partition my hd first.

Unfortunately I tried ubuntu to partition, but failed as it says that I cant and I have to partition it after unmounting. I am new to ubuntu and am not sure what it means


someone suggested me that I could use gparted live cd, but I am stuck up in screen resolution issues and its not able to display

is there anything I can do to resolve and partition the hard disk

also it would be great if you can sugges me the number of partitions that I need to do (for / and /home on linux and also for windows and can something be done for haing a prttion for both o/s'es)

Thanks a lot...

---

### Post by Duck2006 on 2008-04-01
This may help with installing and partitioning.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Tatty on 2008-04-01
You cannot partition a mounted filesystem  - meaning that you cannot partition a drive if you are currently using it.

You will need to boot with a live CD and then run gparted from there to partition your machine.


Its usually reccomended to install windows before ubuntu for ease.  Just be aware that installing windows will probably overwrite your mbr, so you will have to re-install grub afterwards.

---

### Post by binsiram on 2008-04-02
> 
This may help with installing and partitioning.

[http://apcmag.com/how_to_dualboot_vi..._installed.htm](http://apcmag.com/how_to_dualboot_vi..._installed.htm)

Thanks a lot for the link, I started this activity after reading this web page, but gor me the screen just goes off mentioning that 1024X768 is not supported at 85hz refresh rates, unfortunately my crt monitor can suport upto 50hz, i do not know how to change this

> **Tatty said:**
> You cannot partition a mounted filesystem  - meaning that you cannot partition a drive if you are currently using it.

You will need to boot with a live CD and then run gparted from there to partition your machine.


Its usually reccomended to install windows before ubuntu for ease.  Just be aware that installing windows will probably overwrite your mbr, so you will have to re-install grub afterwards.

I used live CD and then did partition and was successful too, but i was not able to load vista may be there's boot partition which i could not turn the boot flag off..

Any help is appreciated...

---

### Post by seshomaru samma on 2008-04-02
just making sure - you created a new NTFS partition right? Vista can't see ext3 file systems
also notice that you will not be able to boot into Ubuntu after your Vista install because Windows will overwrite the MBR. [(here]("http://ubuntuforums.org/showthread.php?t=224351") are instruction on how to reconstruct Grub after a Windows install)

---

