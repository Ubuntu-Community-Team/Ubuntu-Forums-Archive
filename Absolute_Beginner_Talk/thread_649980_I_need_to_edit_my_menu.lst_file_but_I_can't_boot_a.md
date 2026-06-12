---
title: "I need to edit my menu.lst file but I can't boot and OS to edit it"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Token-Ring on 2007-12-25
I recently rebuilt an old computer and decided to dual boot Ubuntu and XP on it, I am new to linux and the best way to learn is to try things out. I followed all the dual boot procedures, but due to hardware mix up I had to install both OS's on the hard drive labeled hd1 instead of hd0. GRUB will not boot Ubuntu because its menu.lst file tells it to look for Ubuntu on hd0 not hd1. All I need to do is change that entry in the menu.lst file from hd0 to hd1, but to change it I either need to get into Ubuntu or XP (I added the ext3 driver for XP) and edit that file. But since the menu.lst file is set wrong I can't boot into an operating system to edit the file. I tried to edit the file from the Ubuntu live CD,  but I doesn't allow me to edit things on the computers hard drives. I can us the XP recovery console to fix my windows MBR and get into windows, but that removes the GRUB portion and I can't boot into Ubuntu so that would defeat the pourpus. 

My question is, how can I edit the menu.lst file from a live CD or floppy? I have seen many topics on edit the menu.lst file, but none on editing it without a working operating system. 

-Thank you for any help

---

### Post by taurus on 2007-12-25
You can edit from the LiveCD.  Make sure you use sudo/gksudo like

```
gksudo gedit /where_you_mount_the_harddrive/boot/grub/menu.lst
```

Otherwise, install fs-driver in XP and edit /boot/grub/menu.lst from XP then.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Token-Ring on 2007-12-25
I think I might have another problem because GRUB is still returning error 17 when I try to boot my computer. So I am going to list my set up and see if anyone can help.

The computer had 2 hard drives 

fd0 has 3 partitions:
	-1 = NFTS has windows XP home on it
	-2 = ext3 my linux partition
	-3 = swap partition

fd1 is a large drive my father uses for backing up all the other computers in the house, that’s why I need XP on the primary partition. 

I have tried every combination of hard drives and partitions in the menu.lst file for GRUB but I can’t get the computer to not return the error 17. Is there anything else I can try?

---

### Post by tact on 2007-12-25
> **Token-Ring said:**
> ...but due to hardware mix up I had to install both OS's on the hard drive labeled hd1 instead of hd0. GRUB will not boot Ubuntu because its menu.lst file tells it to look for Ubuntu on hd0 not hd1. All I need to do is change that entry in the menu.lst file from hd0 to hd1, but to change it I either need to get into Ubuntu or XP

To get yourself booted into ubuntu (I assume from what you have written that you can get grub up but it points ot the wrong partition)....:
1.  press escape if needed (hidden grub menu option set?)
2.  with the grub menu in front of you use up/down arrows to select the ubuntu option.  press "e" to edit the line.
3.  up/down arrow to highlight the line that looks something like "HD (0,0)"   and press "e" to edit.
(the line may different to HD (0,0).  The "zero,zero" refers to "first drive, first partition" so edit to suit where you installed ubuntu.

4.  "enter" exits the edit mode.
5.  press "b" to boot what you have just set.

The changes you make here are NOT permanent. If you power off the machine and power on again you are back where you started.  So do not be afraid to experiment and do a trial & error series of edits and reboots til you get it right.

To make permanent changes - Once you are booted into ubuntu:
1.  delete the existing /boot/grub/menu.lst (or just move it out of the way if you want to keep it for reference)
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.broken01
```

2.  with menu.lst deleted or out of the way, you run update-grub and it re-creates menu.lst.  It should find your XP and ubuntu partitions and set up for dual boot automatically.
(You must let update-grub do the changes to menu.lst in this case to pick up all the correct partition UUIDs etc)
```
sudo update-grub
```

---

### Post by tact on 2007-12-25
You cannot fix this by editing /boot/grub/menu.lst manually.  You need to boot into ubuntu (process described above if you can still get to the boot time grub menu) and then let update-grub recreate the menu.lst

Further...if you have made changes to MBR and can no longer get to the boot time grub menu then you will have to download/burn the ubuntu alternate installer CD.   Boot from that alternate installer LiveCD and select the menu item "Rescue a Broken installation".

Ciao

---

### Post by shareMenaPeace on 2007-12-25
You could also use this GRUB SUPER DISC, to repair GRUB.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

