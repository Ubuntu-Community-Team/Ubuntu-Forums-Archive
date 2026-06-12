---
title: "problems dual booting Windows XP and Ubuntu"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by winbley1530 on 2007-10-29
The problem is when I install Ubuntu 7.10 from the live CD and reboot (no problems with the actual install). I do not get the option to select which OS I would like to boot into all it does is boot into Windows. Any help would be great since I don't know what I need to do to fix this. Also here is what my partitions look like:

sda - 500GB
sdb - 300GB
sdc - 250GB
         sdc1 - ntfs - 150GB
         sdc2 - SWAP - 2GB
         sdc3 - /boot - 100MB
         sdc4 - /        - rest of the free space

Disks sda and sdb are set up in a raid 0 and are formated as a NTFS partition. I have also noticed when I'm going through the install for Ubuntu and on the last screen I click on advance to show where grub will be install, its showing hd0. I'm thinking it should say something else but I'm unsure. 

Thanks for the help

---

### Post by meindian523 on 2007-10-29
hd0 means that Grub has been installed to Master Boot Record.(MBR)

To get options you can edit your menu.lst file.Find it here:/boot/grub/menu.lst
Enter in terminal:
```
sudo gedit /boot/grub/menu.lst
```

Change your timeout options to some number of seconds and the default option to whatever entry you want.Find both these options in the beginning of the file under appropriate comment lines.

---

### Post by carverj on 2007-10-29
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
follow the advice in this thread to restore grub menu
meindian523 advice works for changing the contents of the grub menu once restored!
Have fun!!

---

### Post by meindian523 on 2007-10-29
I guess his problem is that the timeout is too low and the Windows option is the default option in his menu.lst,so he hardly has a chance to register(in his mind) the menu and select Ubuntu before Windows boots up.

Ah,an edit:If the problem description is correct and you can't access Ubuntu due to speed of booting,you might have to use the Live CD to access your menu.lst.For that you will have to mount your / partition(or /boot if you have one) in the Live CD...........

---

### Post by winbley1530 on 2007-11-01
thanks for the help, adjusting the timeout did help out in the end, but restoring Grub did the trick.

---

### Post by meindian523 on 2007-11-01
Please mark your thread as solved.

---

