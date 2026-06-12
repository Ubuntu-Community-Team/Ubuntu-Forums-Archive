---
title: "Attempt at full installation on older machine"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by xzentric on 2006-05-17
Hello All
I have come to Linux because of the philosophy of freedom of access to knowledge and tools.  I have reasonably bodged my way through to a basic lay-person's understanding of 'using a computer' for everything from graphic design and Office work to setting up and maintaining ms setups and networks.  Help files and the internet have been the only way of finding out what I've needed to know (and what little I do know... ;)   Well I've chosen Ubuntu, will Ubuntu choose me? 

Here goes...
 
First stage complete,
computer will now reboot,
ask a few remaining questions and install more packages... 
finishing the installation...
booting from hard disk...
GRUB loading please wait... 
Error 18... hang:???: 
:( 
Seems not to be - yet...
 I'll bodge along and hopefully some 'MagicGenie version 1.6.21' will pop up with all the answers for me - and the meaning of life and the answer to the question: What for? 

Jahmon

---

### Post by az on 2006-05-17
Grub cannot get it's information about your hardware from the linux kernel since the linux kernel is not loaded yet.  It has to get information from your motherboard's BIOS.

BIOS can be pretty dumb.

In this case, your bios is not able to see very much of your hard drive.  It can only see the first few cylinders.  That's fine if the kernel image (the file) is on the beginning of your drive.  In your case, it is not and grub cannot load the kernel because it has no information as to where it is.

You can do se veral things to remedy this.

1.  Go into your bios settings and see if you can make your motherboard use LBA or some other setting which may permit BIOS to see more of your drive YMMV - it depends on your hardware)
2.  Change some jumper settings on the hard drive itself so that the above can happen.
3.  Repartition your drive so as to include a /boot partitoin at the beginning of the drive so that bios will always be able to find it.

There may bo other tricks you can do, but I can't think of them right now.

After changing bios segttings or jumpers, you can try to boot the installer in rescue mode and reinstall grub again to see if it works.

Once you are chrooted into your linux partition:

run
grub-install /dev/hda
reboot




See here:
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

### Post by xzentric on 2006-05-17
Thanks for the info Azz, will check out the link

---

