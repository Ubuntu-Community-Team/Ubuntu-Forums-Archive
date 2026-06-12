---
title: "This little thing is kicking my butt...menu.lst"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by poppers1957 on 2007-06-17
This seems too tricky for me and many others, some really smart or observant person may get it.

Okay, I will try this one more time.  I just don't like machines kicking my A$$
Here is my menu.lst.  Everything works except the windows.  I get an error message that say to remove disks and press any key to reboot.  I really don't care if it ever works.  But in the real world, my son plays games on it, and When I put Ubuntu or PCLinuxOS on other peoples box, I want the boot loader to give them the choice, and not have to go into bios.  I always load any Linux distro after I have disconnected the existing hard drives.  Why?  Because the boot loaders have given me grief before, and trust this method more.   
The Install of all three Linux Distros was done with the HD as IDE Master.   Reconnecting after install the Windows 
HD is IDE 1 Master.  An extra HD for fat32 storage is IDE1 Slave.  The Linux HD Is IDE2 Master, and the CDROM is IDE2 Slave.  


timeout 30
color black/cyan yellow/cyan
gfxmenu (hd0,2)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title PClinuxOS
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hdc3 acpi=on resume=/dev/hdc5 splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title PClinuxOS-nonfb
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hdc3 acpi=on resume=/dev/hdc5
initrd (hd0,2)/boot/initrd.img

title PCLinuxOS failsafe
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hdc3 failsafe acpi=on resume=/dev/hdc5
initrd (hd0,2)/boot/initrd.img

title Ubuntu Feisty Fawn
kernel (hd0,0)/boot/vmlinuz-2.6.20-16-generic BOOT_IMAGE=Ubuntu_Feisty_Fawn_edit root=UUID=3cca8b7f-da04-4def-9f33-081abcf27824 ro quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.20-16-generic

###Don't change this comment - YaST2 identifier: Original name: MEPIS at hdc4, kernel 2.6.12-1-586tsc###
title MEPIS Version 3.3.2
kernel (hd0,3)/boot/vmlinuz-2.6.12-1-586tsc root=/dev/hdc4 nomce quiet splash=verbose vga=791
initrd (hd0,3)/boot/initrd.img-2.6.12-1-586tsc

title WindowsXPmap
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1



*************************************************************************************
I have also tried these with no avail.

title windows2,0
root (hd2,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title windows01
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1
***************************************
Now I really believe there is a way to list this so Windoze boots from the list, but I am just not getting it.  Either I am getting old or tiered or can't get outside the box enough.    I will honestly send someone $12.68 if they can get me the right way to make this boot.  Again I CAN boot Windows by changing the boot order in the BIOS.

---

### Post by leibowitz on 2007-06-17
A little more details could be helpfull.

Where is GRUB installed ?

What is the structure of the windows partitions ? (May be you just have one parition on the HD1 Master disk ?)

Anyway, I would say root (hd0,0)  to boot the windows disk.

And I really don't know what this is :
> map (hd0) (hd1)
map (hd1) (hd0)

seems strange to me.

Anyway, try with root (hd0,0)

---

### Post by alienexplorers on 2007-06-17
I have had trouble booting Windoze from anything other than (hd0,0).

---

### Post by confused57 on 2007-06-17
You could try:

```
title windows2,0
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1
```

---

### Post by poppers1957 on 2007-06-17
Thank you confused57.  I was at another forum looking and I found this thread....[http://www.vectorlinux.com/forum2/index.php?topic=3378.0](http://www.vectorlinux.com/forum2/index.php?topic=3378.0)   It was exactly like you suggested except the sd1 I changed to hd1 etc.... I did that, and it worked.   I came right back here to let anybody know it got solved.  So I guess between you and sa3atsky @ VL forums you guys will have to split the $12.68.  I used My windoze calculator and it comes out to $4.00 each right?   ;)   Thanks so much for your time and help.

---

### Post by poppers1957 on 2007-06-17
> **leibowitz said:**
> A little more details could be helpfull.

Where is GRUB installed ?

What is the structure of the windows partitions ? (May be you just have one parition on the HD1 Master disk ?)

Anyway, I would say root (hd0,0)  to boot the windows disk.

And I really don't know what this is :
map (hd0) (hd1)
map (hd1) (hd0)

seems strange to me.

Anyway, try with root (hd0,0)

Sorry I was vague on that, but it is solved now.  Yes it was one partition on hd1.   The map map thing is a way of convincing windows it was there before the Linux install, according to some forums.  Here is what the final working menu.lst was for windoze to boot from it.........

title windows XPee
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

I appreciate your time.

---

### Post by leibowitz on 2007-06-18
Thanks for trying to explain to me.

But I still don't understand many little things (like why is it hd2, I don't get it)

Anyway, it's cool you made it.

---

### Post by Adramelech on 2007-06-18
root(hd2,0)

root change the booting partition, in this example, the boot partition is 0 on hd2 hard disc, **grub starts counting from 0**, if you have windows on your first hard drive, first partition, it should be root(hd0,0).

Windows thinks it is the only OS in the computer, so you need to change stuff to trick it:

map (hd0) (hd2)
map (hd2) (hd0)

those 2 lines make windows on hd2 thinks it is installed on hd0

chainloader +1

Is a way to tell grub theres another another boot manager (windows one) that is going to take control.

thats pretty much the info you need to add a windows entry on menu.lst

---

### Post by leibowitz on 2007-06-18
Ok, that's clear.

Thanks :-)

---

### Post by confused57 on 2007-06-18
> **poppers1957 said:**
> Thank you confused57.  I was at another forum looking and I found this thread....[http://www.vectorlinux.com/forum2/index.php?topic=3378.0](http://www.vectorlinux.com/forum2/index.php?topic=3378.0)   It was exactly like you suggested except the sd1 I changed to hd1 etc.... I did that, and it worked.   I came right back here to let anybody know it got solved.  So I guess between you and sa3atsky @ VL forums you guys will have to split the $12.68.  I used My windoze calculator and it comes out to $4.00 each right?   ;)   Thanks so much for your time and help.
Glad you were able to get it working...$12.68/2 = $4.00...yep, you used the MS calculator.

---

