---
title: "[SOLVED] Grub &amp;amp; WIN XP"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-12-16
Well i had ubuntu on my pc bt decided to dual boot so i used the Gparted and shrink my hardisk then installed XP on a second partition. well everything went of well and after XP install, GRUB was not found so i followed this thread
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

and installed Grub again, now GRUB only see my ubuntu OS bt there is no XP os showing. what do i need to do again so my XP OS shows up on GRUB.

---

### Post by Existentialist on 2007-12-16
I'm sure there is a way from the GRUB menu thats easier, but the way I did it was to edit grubs menu

>sudo nano /boot/grub/menu.lst

and add:

title Microsoft Windows XP Professional
**root (hd0,1)**
savedefault
makeactive
chainloader +1

to the end, after the ubuntu and memtest items.  The only thing that would be different with yours is the part in bold.  The first number indicates which hd, the second, the partition of windows.  So I believe for you it would be:

root (hd0,2)

I'm sorry I'm not 100% sure on this its been a while since I had this problem.  Just thought I would post a solution in case nobody got back to you quickly with a better one.

---

### Post by Da King on 2007-12-16
to be on a more safer side, when i GRUB FIND, the result was (hd0, 0) which was for my ubuntu i guess, my hard disk is on one and i have partition it now, how do i know the partition number of the xp os?

anyways i will try ur own, i hope it dont bring my system down tho, i will let you know the results soon.

Thanks in advance tho. 

i forgot to mention on my GRUB MENU, this is what shows: 

```
UBUNTU 7.10 KERNEL 2.6.22-14-GENERIC
UBUNTU 7.10 KERNEL 2.6.22-14-GENERIC (RECOVERY MODE)
UBUNTU 7.10 MEMTEST86+
```

im thinking the windows partition wod be on the (HD0, 1) u think im right?

---

### Post by Existentialist on 2007-12-16
If it's wrong it just wont boot the windows option, as long as you don't change the Ubuntu menu items.  The best way to find this is to run:

>sudo fdisk -l

It will list all partitions on the drive and their partition type.  Find the ntfs one and look at what number it is, something like /dev/sdaX.  But since grub starts from 0 just subtract 1 from that number, and put that in root(hd0,X)

Sorry I wasn't in linux before or I would have checked this for you the first time.

---

### Post by Da King on 2007-12-16
my Bad!! i installed my xp as a FAT32. u think that will make any differences or that is the reason the grub is not seeing it?

---

### Post by Existentialist on 2007-12-16
The partition type shouldn't make any difference.

---

### Post by seventhc on 2007-12-16
I think if you open Gparted it will display the drive numbers (hda1 or sda1 or whatever they will be)
or  put this in the terminal 
sudo fdisk -l
But I think you might want to read about grub a bit too.
If you installed xp first and then ubuntu it would be in grub, but since you installed xp after ubuntu you need to add it to grub.

---

### Post by Da King on 2007-12-17
oh well then i guess i will add it to the grub menu as u said earlier. i will let u know the results soon. 

WISH ME LUCK:KS

---

### Post by seventhc on 2007-12-17
Good Luck :cool:

---

### Post by Da King on 2007-12-17
well i booted my pc and press ESC on the grub page so the grub menu came and i press C to go to the command line, then i

SUDO FDISK -l  and it says UNRECOGNISED COMMAND

i  sudo nano /boot/gub/menu.lst amd i again, UNRECOGNISED COMMAND. 

im i not doing the right thing?

---

### Post by teryowen on 2007-12-17
you dont type the sudo fdisk -l in the grub prompt instead in terminal once your booted into ubuntu or a live cd.
same thing goes for editing the menu.lst file do it from terminal in ubuntu

---

### Post by Da King on 2007-12-20
YAAAAAY!! :guitar:I DID IT. Thank soo much guys. U were all really helpful. i got the :popcorn:
why dont u bring the beers so we chill:lolflag:

---

