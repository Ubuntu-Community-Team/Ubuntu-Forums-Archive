---
title: "Grub boots Edgy but Error 21 on XPpro"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Iluvpie on 2007-04-03
Have been running Edgy for months now, no prob.
The other day I did the automatic updates that was indicated at the top of the screen. Now I cannot boot XPpro but I can get to Grub and Ubuntu works fine. But selecting XPpro option brings up "Error 21: Disk not found".

---

### Post by al7kz on 2007-04-03
The upgrade may have installed new kernels which overwrote the /boot/grub/menu.lst file. You may have to edit that file. Do you have both SATA and PATA drives. What is the output of $sudo fdisk -l. What is the entry in menu.lst for XP. What is /boot/grub/device.map. If you get the grub menu at boot, try booting XP from that by hitting "c" at the menu then:
grub> rootnoverify (hd0,0)  (or wherever XP is)
grub> makeactive
grub> chainloader +1
grub> boot

If XP isn't on the first hard drive (hd0) then you have to remap it to (hd0). Say it's on (hd2), the third hard drive:
grub> rootnoverify (hd2,0)
grub> map (hd0) (hd2)
grub> map (hd2) (hd0)
grub> makeactive
grub> chainloader +1
grub> boot

---

### Post by Iluvpie on 2007-04-04
Using 'c' only brings me to the grub command prompt and I cannot access XPpro there either.
Below is the menu.lst I have.


title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify		(hd1,0)
savedefault
makeactive
chainloader	+1
boot

---

### Post by al7kz on 2007-04-04
OK. That grub command prompt is your friend and gives you a really powerful troubleshooting tool if you want to take the trouble to use it. 

At the grub prompt, type (don't type the "grub>" part, that's just the prompt):

grub> root (

then hit tab. What to you get? Does it give a list of possible disks? Please give us that output. 

Type in the first hard disk as follows:

grub> root (hd0

then hit tab twice. Tell us what the output is. Do that for the second hard drive:

grub> root (hd1

and hit tab twice; what do you get?

You should get a list of partitions, showing where grub thinks XP is and linux is. XP shows up as type 0x7. Give us that data. 

This is all explained in the Grub Manual. It has a lot of good info in it but it's hard to read.  

Hope this helps. Please report back with what you found. Thanks.

---

### Post by Iluvpie on 2007-04-04
These are the responses for disks Grub can see.

Grub> root ( TAB
Possible disks are 
fd0 fd1 hd0


Grub> root (hd0 TAB TAB
Partition number:0 file system type unknown, partition type Ox7
Partition number:1 file system type ext2fs, partition type 0x83
Partition number:2 file system type unknown, partition type 0x82

I do not have hd1, hd2, etc

---

### Post by al7kz on 2007-04-04
OK good, now type at the grub prompt (don't type "grub>" that is the grub prompt, and hit enter after each command:

grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

---

### Post by Iluvpie on 2007-04-04
Results using Enter:

grub> rootnoverify (hd0,0)               
    nothing happens returns to prompt Grub>
grub> makeactive                          
   nothing happens returns to prompt Grub>  
grub> chainloader +1                    
   Error 11: unrecognized device string  
grub> boot                                     
   Boots up Xppro

At least we now know that the windows program works
But Grub on startup will not boot XPpro when selected- provides error 21

---

### Post by Iluvpie on 2007-04-04
I figured it out, 

I changed the drive numbers to what was actually on the machine.
Besides the updates, I had removed a drive that was not working, but it was a slave on IDE2, and I did not think that the Grub was pointing to it in any way when Ubuntu was installed as the original remaining drive was the XP partition.  I am new to Linux, but I started thinking logically what the 0 and 1 actually stood for in that senario.   

Thanks again, you got my brain working.

---

