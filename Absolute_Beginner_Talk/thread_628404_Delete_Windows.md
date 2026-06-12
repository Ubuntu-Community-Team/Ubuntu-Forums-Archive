---
title: "Delete Windows"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by JohnPta on 2007-12-01
My PC set-up is as follows: HD1 is windows(80Gb) and HD2 is Ubuntu(20Gb). Now I want to take out the hard-disk  for windows and delete windows. Than I want to copy the content from hd2 to hd1 (it is bigger) So HD1 must be bootable, it will be Ubuntu. After that I want to install windows on the small HD and make it HD2. 
However Grub is in the MBR of HD1. How can I change the boot sequence, so grub will be looking for Ubuntu on HD1(80Gb) and windows on HD2(20Gb)?

---

### Post by Don1500 on 2007-12-01
> **JohnPta said:**
> [LEFT][LEFT][CENTER]My PC set-up is as follows: HD1 is windows and HD2 is Ubuntu. Now I want to take out the hard-disk  for windows and delete windows. Than I want to copy the content from hd2 to hd1 (it is bigger) So HD1 must be bootable it will be Ubuntu. After that I want to install windows on the small HD and make it HD2 [/CENTER][/LEFT][/LEFT]

Is all you want is for Ubuntu to be the prime boot? and windows to be on the smaller partition, or do the names really matter?

You can use Gparted to readjust the partition sizes.
And you can edit Menu.lst (/boot/grub/menu.lst) to place Ubuntu as the default system of a twin boot.

---

### Post by JohnPta on 2007-12-01
I actually also want to swap the HD's The 80Gbb which is now Windows should become Ubuntu and the 20Gb which is now Ubuntu will be reformatted and the basic xp will only be loaded there to drive my modem fax, 
Rgrds Jan

---

### Post by PmDematagoda on 2007-12-01
I believe that this should be enough:-

1) Install XP on he second HDD.

2) Install Ubuntu on the first one.

I do not think you will have to worry about the MBR since according to what I have experienced, the MBR stays in one drive unless you move it yourself to another one. So you can do the swap while just sticking to the default BIOS settings.

---

### Post by edm1 on 2007-12-01
It's going to be a risky task but it's possible. I would recommend booting from a live cd then using gparted to delete you windows partition, clone the ubuntu partion over to HD1, delete ubuntu partion from HD2. Then you'll have to edit /boot/grub/menu.lst and resetup grub. Sorry for the lack of detail but i'm supposed to be revising. I'd spend a little time looking into it before you go ahead. Backup everything!

EDIT: It'll be alot easier to do as PmDematagoda said.

---

### Post by bodhi.zazen on 2007-12-01
> **JohnPta said:**
> My PC set-up is as follows: HD1 is windows(80Gb) and HD2 is Ubuntu(20Gb). Now I want to take out the hard-disk  for windows and delete windows. Than I want to copy the content from hd2 to hd1 (it is bigger) So HD1 must be bootable, it will be Ubuntu. After that I want to install windows on the small HD and make it HD2. 
However Grub is in the MBR of HD1. How can I change the boot sequence, so grub will be looking for Ubuntu on HD1(80Gb) and windows on HD2(20Gb)?

You can manage your partitions with gparted, but you should do this from a live CD.

GParted:Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

When you move your partitions you will need to manually edit /etc/fstab and /boot/grub/meun.lst

This should give you the general idea : 

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)


This may also help :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

So you can likely move your Ubuntu partition and update /etc/fstab and booot/grub/menu.lst , then install windows, then re-install grub

---

### Post by quandary on 2007-12-02
The ways described above are way risky and complicated for a newbie.
I suggest you install Ubuntu on the first HD. This will overwrite Grub.

Then you boot into your new Ubuntu. Then you can move the data and config files from the old partition to the new one. Don't forget emails.

Afterwards, you can install XP on the second hd. If Windows overwrites the MBR, you will have to put grub back there.
Also, you have the problem that you install Linux first, and XP afterwards, which is more complicated than vice-versa.
For instructions, see: 
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)



To add the XP partition to Grub, you have to edit menu.lst. 

On the command line, type:
sudo gedit /boot/grub/menu.lst

---

