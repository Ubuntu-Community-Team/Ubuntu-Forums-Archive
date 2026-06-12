---
title: "possible FIX to: problem with GRUB and MBR"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Arizon_Dread on 2007-06-23
Hello!

I just installed ubuntu a few minutes ago and got a problem with GRUB and master boot record.
I changed the order of harddrives (have one IDE windows drive and one SATA linux drive) in the boot menu in bios. this was not a good thing to do, i noticed. ;)

Got the problem: 
```

Loading Grub, please wait...

Error 15.

```
and then it just hanged there.

I tried to find out how to change the mbr or grub, didn't think my change of hdd order mattered, but after an hour of googling, i thought that this might be the problem, so I changed it back.

could also add that I tried with:
```

sudo grub

grub> find /boot/grub/stage1

Error 15: file not found

```

then I changed the boot order of the harddrives back to what it was at first and it worked.

If you add a new harddrive, the master boot loader and master boot record is located on the old drive, therefore you can't begin to boot from the new drive if you don't change the mbr.

just some n00b info. maybe some one will be helped by this.


CORRECTIONS TO THIS IS VERY WELCOME since I am a n00b :D

//Arizon

---

### Post by logos34 on 2007-06-23
> then I changed the boot order of the harddrives back to what it was at first and it worked.

If you add a new harddrive, the master boot loader and master boot record is located on the old drive, therefore you can't begin to boot from the new drive if you don't change the mbr.

just some n00b info. maybe some one will be helped by this.

you're pretty much on target...The debian installer is programmed to put Grub stage1 bootloader by default on the MBR of the first detected drive in the BIOS hard disk boot order, or '(hd0)'--you CAN manually specify another location though--and Grub seems 'hardwired' to list IDE drives before any sata, scsi or USB drives...Which means that regardless of the actual hard disk boot order, any IDE hard drive present will always be designated hd0 and THEN the sata/scsi/external usb drives, in the order they appear in the bios.

This. of course, overwrites any bootloader present on the main drive--usually windows--but normally this isn't a problem because grub is a versatile bootloader.  But it causes confusion because most first-time linux users expect to boot to grub on the linux install target drive and change the boot order the bios after install.  The one advantage to having grub on the windows drive in a dual drive-dual boot setup is that there are fewer problems getting windows to start up (it's all down to a quirk of windows which refuses to boot off a non-first hard disk--it thinks it owns your machine and demands to be FIRST! So you have to trick it by editing your windows entry in mneu.lst by making it THINK it's on the first disk.)

Alternatively, you can just specify at install time that it go on the linux drive, leaving windows drive untouched, and then boot to the linux drive.  Or, in your case, just reinstall grub to the mbr of the linux drive, and restore windows bootloader to the mbr with fdisk /mbr or fixboot methods.

---

### Post by molly_001 on 2007-06-23
Great stuff, logos!

I'm going to start following you around, Mister. (virtually)
I could learn a lot !

---

### Post by logos34 on 2007-06-23
oops..poof!  that was clumsy.  well forget that edit

---

### Post by molly_001 on 2007-06-23
Yes, he truly is.  herman even links his site to mine (for my dual boots pages).
But I've not seen anyone explain that as well as you did, and I didn't know some of it anyway so it was  great post. (if you ask me)

---

### Post by logos34 on 2007-06-23
> **molly_001 said:**
> Yes, he truly is.  herman even links his site to mine (for my dual boots pages).
But I've not seen anyone explain that as well as you did, and I didn't know some of it anyway so it was  great post. (if you ask me)

thank you.

---

