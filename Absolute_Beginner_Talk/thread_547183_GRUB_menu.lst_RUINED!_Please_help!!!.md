---
title: "GRUB menu.lst RUINED! Please help!!!"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-09-09
Hi there, 

I am writing from a liveCD
I must have screwed my menu.lst file by updating my grub (I wanted to get rid of the MP-BIOs bug notice and thus I put noapic in the default settings in menu.lst and then I typed update-grub). I guess that screwed everything.
I have the backup of menu.lst in my boot partition but I can't access it from the liveCD. How the hell am I supposed to find it?
I tried mount /dev/hda3 /media/bootmount but the new directory media/bootmount doesn't show anything.

Please help!!!!!!!!!!!!!
I need the computer to work!!

Cippa Lippa

---

### Post by Jose Catre-Vandis on 2007-09-09
Assuming hda3 is where your ubuntu install exists try

```
sudo mkdir /media/bootmount

sudo mount /dev/hda3 /media/bootmount
```

You need to be root/sudo to mount the directory and edit files

---

### Post by bruce2000 on 2007-09-09
how to install grub from a livecd: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Cippa Lippa on 2007-09-09
That is what I did. 
It tells me that it is mounted but there is nothing in it.
If I type fdisk -l it tells me nothing
It seems it can't see the partitions in the hard drive . I can see them with qtparted though....

help!

---

### Post by Cippa Lippa on 2007-09-09
I think the update-grub thing basically deleted the whole content of the boot directory.
So, due to this the grub restoring doesn't work

any ideas pals?

Cippa

---

### Post by bollix47 on 2007-09-09
What does

```
sudo fdisk -l
``` 

give you?

---

### Post by Jose Catre-Vandis on 2007-09-11
Have you tried mounting any of your other partitions, and if so can you see files in the mount? If so, why can you not see files in /dev/hda3? It is unlikely that your "update-grub" command would have wiped/or corrupted the whole filesystem, so if you can mount it, and this was indeed your ubuntu install, you should be seeing files, no matter how knackered your boot directory and files are.

What happens if you just boot from your hard drive?

Are you dual/(or more) booting? If so, can you boot to an alternate OS and access your ubuntu from there?

If you have enough unallocated space, try installing ubuntu again as a separate OS, and see if you can access files to fix them to boot from the new MBR grub?

---

