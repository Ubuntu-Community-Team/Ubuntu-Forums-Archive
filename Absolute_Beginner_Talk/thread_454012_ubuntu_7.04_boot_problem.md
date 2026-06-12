---
title: "ubuntu 7.04 boot problem"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by m1e1w1 on 2007-05-25
before posting, i did a search on all fourms to see if i could find a solution to my next problem ive encountered. Had no luck with that, so heres my post:

I installed Ubuntu 7.04 FF, with some difficulty useing the live CD. I had to set my VGA size to max, and add noapic noirqdebug to the boot line just to get the installer desktop.
I installed Ubuntu, along side windows vista. i manualy partitioned the drive to include 3 partitions.
1-windows vista
2-ubuntu
3-swap
when the install finished and ejected the disk, i rebooted the machine. It loads GRUB with the following options:
kernal (with normal boot)
kernal (recovery mode)
memory test
windows vista/longhorn
i picked default, to load kernal for ubuntu, and it procides to the orange bar loading the system. half way through the bar progressing from left to right, the system locks up. I can still boot ubuntu with the live cd, and the modifyed boot line, but it wont boot normaly from the hard disk drive. I can also boot windows vista normaly.

what do i need to do, to get ubuntu to load from the hard drive normaly?

---

### Post by Paperclips4u on 2007-05-25
It seems like something was corrupted during the install.

Possible solution. Shred /dev/hda1 (linux partition) and reinstall. Luckily it doesn't take very long to do a reinstall. Make sure your disc has no errors though. You can test it when you first boot to the intall disc. The option is somewhere below "Start or Install Ubuntu."

---

### Post by m1e1w1 on 2007-05-25
takeing the advice, i booted with the live cd, and did a disk integrity check for flaws and errors. those results came back clean. (the physical condidtion of the disk is also flawless)

do i reformated the lunix partition completly and reinstalled ubuntu. it still hangs up when the orange loading bar gets half way, from left to right.

anything else come to mind that might be a fix?

---

### Post by honeydew on 2007-05-25
just for shits and giggles try adding 
```
irqpoll
``` 
 to the boot parameters.. this sounds almost identical to the experience i was having a few weeks ago.  Also, get rid of quiet and splash.. this way you can see whats going on during the boot up.. be sure to let us know!

-be well.

---

### Post by m1e1w1 on 2007-05-25
umm... how do i boot from the hard drive kernal, and make boot ajustments?
im willing to try the suggested step, but not sure how to do it. it wont do my any good booting from the live cd, to find out whats wrong....

---

### Post by confused57 on 2007-05-25
> **m1e1w1 said:**
> umm... how do i boot from the hard drive kernal, and make boot ajustments?
im willing to try the suggested step, but not sure how to do it. it wont do my any good booting from the live cd, to find out whats wrong....

What you can do is highlight your Ubuntu entry in the grub boot menu, press "e", then add your boot options to the kernel line, then press "b" to boot...this is temporary if it works, but you can edit your menu.lst to make it permanent.

---

### Post by m1e1w1 on 2007-05-25
thanks for that step! it worked to get me into ubuntu from the hard drive. i removed the quite splash code, and added that irqpoll.
my system did not encounter any errors though.... loaded right up.

so what do i need to edit, and how do i edit it to do this every boot up?

---

### Post by confused57 on 2007-05-25
> **m1e1w1 said:**
> thanks for that step! it worked to get me into ubuntu from the hard drive. i removed the quite splash code, and added that irqpoll.
my system did not encounter any errors though.... loaded right up.

so what do i need to edit, and how do i edit it to do this every boot up?

Open a terminal(Applications---Accessories---Terminal), enter:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```

then to edit:
```
gksudo gedit menu.lst
```

Then just add the boot options to your kernel line in your menu.lst,  you'll also need to make changes in the defoptions line:
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)
you need to do this because a kernel update will run update-grub & change your kernel options accordingly.

---

### Post by m1e1w1 on 2007-05-25
alright i made those changes. thanks for the help

---

### Post by honeydew on 2007-05-25
just a question are you running sata hardware? Im trying to figure out what this bug is caused by...

---

### Post by m1e1w1 on 2007-05-26
no, im running ata/eide hardware. from the looks of what i can tell, its something to do with firmware somwhere in the machine.

---

