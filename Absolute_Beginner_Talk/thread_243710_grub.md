---
title: "grub"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by swardfox on 2006-08-25
HI 
 I messed the GRUB and deleted the linux partition...now I cant boot the windows XP, ERROR 17. 
  I m wondering if i install GRUB again would it fix the problem..
 but i cant when i try this command

find /boot/grub/stage1

it says file not found..

can anyone tell me how to fix this problem pls
thanks

---

### Post by harisund on 2006-08-25
First and foremost, do you know the layout of your hard disk? 

Basically, tell me if you are able to answer the following 

Assuming you are dual booting, your hard disk must have partitions. Are you familair with hda1,hda2 and so on? 

If so, do you know where your Windows and Linux are installed? 

Are they all primary partitions? If so, we basically will have only hda1,hda2,hda3,hda4 to worry about. If not, it goes to hda5 and beyond. 

Do you have only one hard disk on which both are installeD?

---

### Post by Crosbie on 2006-08-25
If you want to just get Windows working again, best to use an XP CD in repair/recovery mode and do FIXBOOT/FIXMBR.  (Google to be sure, btw.)

---

### Post by harisund on 2006-08-25
Is that what you want? If so, it's quite easy to do

---

### Post by Endwin on 2006-08-25
I take it you are removing Linux and just want windows? If so we can restore the MBR windows uses. Insert an XP installation CD and enter setup mode. Choose the recovery option and boot to the DOS command line. Execute the command ```
FIXMBR
```

If you want to restore grub and reinstall Linux, you can reinstall Linux and it will automatically install grub. 

If you want to use grub and not have Linux, I don't think that is doable, I think it requires /boot to get all the information it needs in order to boot the system and for that you need some basic Linux installed.

---

### Post by harisund on 2006-08-25
Are you sure about that endwin? In one of my machines, grub was in the mbr, but there was no Linux. I ended up manually typing the following every time ```
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

Or perhaps I am missing something?

---

### Post by Endwin on 2006-08-25
As I said I could be wrong (and looks like I am) I can go look for some manual way to install grub if you want/need it. Probably need a live CD mount the drive then install grub.

I know in a linux recovery situation (partly failing hardrive) and you copy stuff to the new drive you can reinstall grub after first finding the name of the bootable drive with ```
fdisk -l
``` then mounting the drive, and finally running the command ```
grub-install --root-directory=/mnt/<NAME OF DRIVE> /dev/<DRIVE BASE>

```

**UPDATE**

It looks like in the ubuntu guide they mention the Super Grub Disk

[http://adrian15.raulete.net/grub/tiki-index.php]("http://adrian15.raulete.net/grub/tiki-index.php")

That may be worth taking a look at for a grub (no linux) bootloader.

---

### Post by true_friend on 2006-08-25
batter for u to fix the mbr from xp cd.
boot from it and go to recvoery mode by pressing R when it gives options ( more than one along with installation option). do not press any button until it asks which windows isntallation u want to logon ( or some thing such kind of message). enter 1 assuming u have only 1 windows installation. there should be one i also use dual boot with ubuntu and my xp installation is 1. so enter 1. u would be asked admin passwd.
then in c:\windows enter command fixmbr. then y and enter. it is ok. restart the system.

---

