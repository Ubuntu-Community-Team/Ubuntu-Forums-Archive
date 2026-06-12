---
title: "Problem Dual Booting Vista and Ubuntu (vista installed first)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by rpzatkof on 2008-01-19
I had two separate partitions on a hard drive both dual booting vista (long story of why that was true) - there was a 150 gb portion and a 10 gb portion and i wanted ubuntu on the 10 gb


i installed ubuntu on the 2nd partition and everything is working fine now with ubuntu and i can see all my old files from vista but when i turn on my computer it boots straight to ubuntu and there is no option in the menu (when you press esc) for vista

i've tried looking around for other options in trying to boot vista but nothing seems to work

help?  what other information do you need?

oh the 150 gb portion of the drive is labled as sda2 in ubuntu when i open it

---

### Post by dstew on 2008-01-19
You may need to add an item to the grub menu to boot VIsta.  To edit the file use the nano text editor from a terminal window:```
sudo nano /boot/grub/menu.lst
```Add these lines below the ### END DEBIAN AUTOMAGIC KERNELS LIST separator:```
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```Quit the editor by ctrl-X, answer Y, hit Enter to save the file. Then reboot and see if you get the Vistsa menu option.

---

### Post by rpzatkof on 2008-01-19
since i first posted this i tried a few different things and now ubuntu wont load unless i go through a cd of super grub recovery disk


it was working fine until i put in the super grub recovery disk and now nothing works unless i go through super grub


however trying what you said earlier vista appears and i click it and an error comes up says invalid file..hold on a few minutes and i will get the exact error

---

### Post by Thund3rstruck on 2008-01-20
Well if you've borked up your grub config you can boot into Vista recovery mode and run [fixmbr]("http://pcsupport.about.com/od/termsf/p/fixmbr.htm"). This will wipe out grub with the Windows bootloader. After Windows is back up and running you can search around for the guides for repairing grub from your live cd.

---

### Post by dstew on 2008-01-21
> however trying what you said earlier vista appears and i click it and an error comes up says invalid file.That probably means that (hd0,0) was not the proper root for Vista. Post the result of **sudo fdisk -l** onto the forum.

---

### Post by munch3 on 2008-03-01
Same problem, now checking weather it'll work

---

