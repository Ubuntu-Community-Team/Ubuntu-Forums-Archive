---
title: "[SOLVED] Big trouble tonite"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-28
The situation.  Two hard drives. The first has windo-ws the second edgy. First drive is quitting. I removed the bad drive and now the second wont boot. I put the bad drive in and the second boots ok. This can't last long so the question is what do I have to do to get the second drive to boot when the first is gone.  I know it has something to do with grub but what buttons do I have to push to get things working. 

Next In the /dev directory is a folder hdd for the cd drive. All of a sudden it's gone and the drive wont work. Any suggestions for that puppy.

Thanks and I sure hope someone knows the answers.

---

### Post by ReaderRat on 2006-12-28
[[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)
This may help....

---

### Post by pizzutz on 2006-12-28
Could it be as simple as changing the jumper on your second drive from SLAVE to MASTER when you remove the first drive?

just thought I'd check.

---

### Post by confused57 on 2006-12-28
> **squrl said:**
> The situation.  Two hard drives. The first has windo-ws the second edgy. First drive is quitting. I removed the bad drive and now the second wont boot. I put the bad drive in and the second boots ok. This can't last long so the question is what do I have to do to get the second drive to boot when the first is gone.  I know it has something to do with grub but what buttons do I have to push to get things working. 

Next In the /dev directory is a folder hdd for the cd drive. All of a sudden it's gone and the drive wont work. Any suggestions for that puppy.

Thanks and I sure hope someone knows the answers.
The first thing you'd probably need to do is install grub to the 2nd drive's mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

e.g., if **find /boot/grub/stage1** returns **root (hd1,0)**, then **setup (hd1)**

make sure your hd jumper settings are correct, as suggested by pizzutz

It probably won't boot up this way, since may need to change the root from (hd1,0) to (hd0,0) and in the kernel line hdb1 to hda1, since you've moved the drive from the slave position to master...you can try this from the grub menu, by highlighting the Ubuntu grub entry, press "e" for edit, make the changes, & then try to boot.

Alternatively, do the live cd to install grub to the hd mbr...leave the hd set as slave, but set your bios to boot first from the slave drive...you'd still need to do the edit grub menu, but all you'd need to change is root from (hd1,0) to (hd0,0)...

If any of this actually works, you'd need to make it permanent in your /boot/grub/menu.lst.  

By setting your Ubuntu drive as master(hda), you may need to edit your /etc/fstab to reflect where the device(s) are located(/dev/hda)...so you may want to try the 2nd method(leave as slave) first.

---

