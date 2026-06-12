---
title: "GRUB crashing"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2008-04-13
I am running Gutsy on a Macbook pro dual booted with rEFIt and Grub, it has been working fine for months with out problems.

However today when i restarted Grub will not load it, it just sits with a black screen reading GRUB in the top left corner and pretty much hangs up their getting hot.

I have tried reinstalling grub from the live cd which has not worked. The gutsy partition is mountable through the live CD and I can access my data.


Any ideas on how to fix GRUB?

---

### Post by cyberdork33 on 2008-04-13
can you check the menu.lst?

how did you reinstall grrub?

---

### Post by Monsoonx27 on 2008-04-13
I can't check menu.lst or i dont know how either one.

I reinstalled grub through the terminal while using the live cd

i opened grub then found the partition using it using the find command.
then installed using su to the partition using it hd(0,3)

---

### Post by cyberdork33 on 2008-04-14
> **Monsoonx27 said:**
> I can't check menu.lst or i dont know how either one.menu.lst is the grub menu config file. if you can boot from the live cd and mount your ubuntu partition, it is located in /boot/grub/menu.lst

> **Monsoonx27 said:**
> i opened grub then found the partition using it using the find command.
then installed using su to the partition using it hd(0,3)

It sounds like the Stage1 loader is installed ok, but it is not finding the stage2 part (which is on your ubuntu partition). 

After using the find command
```
find /boot/grub/stage1
```you should set the root partition as well... ```
grub> root (hdX,Y)
``` before running the setup command. ```
grub> setup (hdX,Y)
```That should point it to the correct location to find stage2 unless the stage2 file is missing!?!?! (look in the same folder as the menu.lst file.

---

### Post by Monsoonx27 on 2008-04-14
the above it exactly what i did first before making this post and it did nothing to fix it

---

### Post by cyberdork33 on 2008-04-14
EDIT:

I would guess that it is an issue with the file on the actual ubuntu partition then.

---

### Post by Monsoonx27 on 2008-04-14
Okay, I just loaded the live cd, i can view all of the appropriate files in the GRUB folder (menu.lst   stage1 stage2 etc)

however now i cannot reinstall grub

when i try

find /boot/grub/stage1    i get error 17 cannot be found so i can't even make it root or set it up

---

### Post by cyberdork33 on 2008-04-14
> **Monsoonx27 said:**
> Okay, I just loaded the live cd, i can view all of the appropriate files in the GRUB folder (menu.lst   stage1 stage2 etc)

however now i cannot reinstall grub

when i try

find /boot/grub/stage1    i get error 17 cannot be found so i can't even make it root or set it up
Well that's not good. Stage2 is loading, and it gives that error.
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Monsoonx27 on 2008-04-14
Thanks for your help, although the problem wasnt solved it lead to complete and total annihilation of my partition which was slowly dieing the more i tried to fix it. I still don't know what caused the issue but i have reformated.

---

### Post by grabbies200 on 2008-04-25
Similar problem here. I used to have gutsy installed via bootcamp and worked fine. I then stupidly cleared ubuntu and put vista for a couple of days. Today i removed vista and restored the hard drive. I then restarted bootcamp. I then installed Heron, but when i tried to reboot it won't find a bootable device.
I tried to install grub manually, but if i do a >grub-install /dev/sda 
i get could not find device for /boot.
I tried to go into grub and find /boot/grub/stage1 but it tells me that the file is not found, even though if i do an ls i can see the file is there.
I then restarted and went into the partition utility of refit and it asked me to resync MBR. I did that and retried to reistall grub, but no luck.
Also from grub if i try root(hd<tab> it cannot find any disks.
I need help.

---

### Post by grabbies200 on 2008-04-25
hi again.
it turns out that the partitioner messed up the mbr.
i found a solution here
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

