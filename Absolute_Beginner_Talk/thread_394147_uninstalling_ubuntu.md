---
title: "uninstalling ubuntu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-03-26
SOLVED

i'm trying to decide whether to make the jump from windows to ubuntu.  the last thing i need to know is how i can *UN*install ubuntu and go back to only using windows if i need to.  could someone help point me in the right direction?  all i find when i search the forums and google is a bunch of people complaining that ubuntu wrecked their system and they want a one-click-fix of how to un-install and go back to the way things were before.  could someone just tell me in a straightforward way how easy it is and how to do it?

---

### Post by Bachstelze on 2007-03-26
Delete Ubuntu partitions with a Live CD or Windows' Disk Manager then restore the Windows MBR (boot from Windows CD, recovery console, fxmbr).

---

### Post by fakie_flip on 2007-03-26
The best way to know how Ubuntu will work on your system before installing it is using a Live cd. That's like giving a car a test drive before buying it. You can check and see what works and if anything does not. Keep in mind that once you have Ubuntu installed, it will run faster than the Live cd, and you won't be able to install the nvidia driver in the Live CD because it uses your ram, not your hard drive, and so your ram will get too full until you reboot again.

---

### Post by locke.dragon on 2007-03-26
thanks.  the only problem is that my dell laptop didn't come with a windows install disk.  :P  i'll have to have them send me one.  how much extra time would it take them to package it with the machine?  LOL!

---

### Post by locke.dragon on 2007-03-26
i'm using the live cd to write this post.  :P  i'm really pleased so far other than the fact that i can't use 1280x800 in the live cd or write to my ntfs windows partition.

---

### Post by fakie_flip on 2007-03-26
Downloading a windows xp iso is much faster from a torrent site like torrentspy.com, but it is illegal (unless you live in a different country maybe), so don't do that.

---

### Post by annda on 2007-03-26
lots of people now do not have proper windows install cd's, only OEM recovery ones. they do not provide a recovery console, but erase/overwrite the entire partition.

i've been looking for a way to format the MBR from linux, but haven't found any. good old lilo could at least restore the boot sector. is there a way to get rid of GRUB? i'm not asking for myself, i don't use win, but this is becoming a serious issue as more and more people dual-boot (largely due to ubuntu's friendliness), and at the same time microsoft puts more and more effort into taking from people the control over their preinstalled systems.

so i'm asking the committed experts here: is there a way to remove GRUB/format MBR without a win install cd? floppies are becoming obsolete too, so many downloadable win98 recovery floppy images are not very useful in this case...

ps. i really believe that not so many people actually want to remove linux, but probably most new users need to know that they can.

---

### Post by fakie_flip on 2007-03-26
> **locke.dragon said:**
> i'm using the live cd to write this post.  :P  i'm really pleased so far other than the fact that i can't use 1280x800 in the live cd or write to my ntfs windows partition.

that can be fixed easily once you have ubuntu installed with these commands. I could not get 69 hz refresh rate on my monitor at 1792x1344 resolution until I installed the nvidia driver and made a few changes to my xorg.conf.

sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

---

### Post by locke.dragon on 2007-03-26
can't you make a windows image from a working windows computer?

---

### Post by Bachstelze on 2007-03-26
You can also grab a Windows CD from a friend and make a copy for yourself. You have perfectly the right to do so since you purchased a license.

---

### Post by locke.dragon on 2007-03-26
i'll see if i can grab one soon.  thanks.  could i use this copy as a live cd to scan my hard-drive for viruses?

---

### Post by deanlinkous on 2007-03-27
> **annda said:**
> 
so i'm asking the committed experts here: is there a way to remove GRUB/format MBR without a win install cd? floppies are becoming obsolete too, so many downloadable win98 recovery floppy images are not very useful in this case...

a win98 (or similar) floppy image can be burned as a bootable CD as well but I havent found any GNU+linux way of wiping the mbr

---

### Post by deanlinkous on 2007-03-27
I would think dd could be used somehow. During install if it created a backup of the mbr then you could have a uninstall button that at least rewrote the mbr and got rid of grub. ????hmmm????

---

### Post by seshomaru samma on 2007-03-27
I think FreeDOS has a fixmbr option
the command there is :
```
fdisk /mbr
```

---

