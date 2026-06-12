---
title: "ruined usb external harddrive!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by josephpford on 2007-08-05
Ok, I don't know exactly what I did, but now my external harddrive is ruined.  I tried to use my external 250gb harddrive in linux and it said something about needing to restart windows 2 times and then I did that and then I went into linux and it said something about mounting it and I don't remember what I did, but not my external harddrive appears to be ruined.  I can't format it in windows (fat32 or NTFS) and in linux I can't get it to work all the time either.  Is there some way I can completely reset to factory settings using linux?!?

Thanks for your help!

~Joe

---

### Post by ugm6hr on 2007-08-05
Sounds like a problem with the partition table.  I can't remember how to fix it - but a bit of searching here on partition table recovery will probably find something useful.

---

### Post by ticklecricket on 2007-08-05
You could try formatting the drive using a graphical tool like GParted.

Or if you want to be classy just run 'fdisk /dev/DISKNAME/' in the terminal

**replace /dev/DISKNAME/ with the location of the disk**

As ALWAYS be super careful before messing aroudn with partitions.

---

### Post by bren on 2007-08-05
and if you want to repair your partition table (and get back any data that was on the drive) then use the utility testdisk (search on here for previous instructions i gave for using this which helped me:)).     Testdisk is available on the gparted LIVECD (which you would have to download and burn first) or in the repositories by means of command 

```
sudo apt-get install testdisk
```

however, if you boot linux from the same hard drivei am not sure testdisk can modify the partition table - use the liveCD in this case..

i also agree with the comment above about investigating the state of your partitions via gparted (Sys-admin-gnome partition editor from Ubuntu [if you have installed] or Ubuntu LIVECD) first before you run testdisk

good luck and let us know how you get on

bren

---

### Post by josephpford on 2007-08-06
Everyone - thank you for your replies.  I am still unable to get the USB harddrive to work, with all the above methods suggested.  

Is there anyway I can provide a dump of the settings of the harddrive so that I may be better able to get help?  I feel that I do not know enough to provide information on what my problem is.

Additionally, is there a program that you know of that I can download that will look at the harddrive and scan it for any problems (I'm thinking of something similar to chkdsk for windows).  I've tried formatting the drive in windows and it always says "the format did not complete successfully".  

I'm really good at hosing my computer.  I wish I were better at fixing it...

Again - thank you everyone for your help.

~Joe

---

### Post by Inxsible on 2007-08-06
> **josephpford said:**
> Everyone - thank you for your replies.  I am still unable to get the USB harddrive to work, with all the above methods suggested.  

Is there anyway I can provide a dump of the settings of the harddrive so that I may be better able to get help?  I feel that I do not know enough to provide information on what my problem is.

Additionally, is there a program that you know of that I can download that will look at the harddrive and scan it for any problems (I'm thinking of something similar to chkdsk for windows).  I've tried formatting the drive in windows and it always says "the format did not complete successfully".  

I'm really good at hosing my computer.  I wish I were better at fixing it...

Again - thank you everyone for your help.

~Joe
Connect your USB drive to the machine and do this.
```
sudo fdisk -l
```Also post the output of ```
gksudo gedit /etc/fstab
```

---

### Post by Inxsible on 2007-08-06
If you dont have any data that you want to retrieve from the disk then you can simply nuke the drive. Use GParted to format it or have a look at [DBAN]("http://dban.sourceforge.net/")

---

### Post by josephpford on 2007-08-07
> **Inxsible said:**
> If you dont have any data that you want to retrieve from the disk then you can simply nuke the drive. Use GParted to format it or have a look at [DBAN]("http://dban.sourceforge.net/")

I tried to use GParted on the drive, but it never stopped scanning.  I think it has to do with the fact that the USB drive connected to the computer is in an unformatted state.  I used testdisk_win (because I can't get the USB drive to become recognized in Linux sometimes) to completely nuke the drive, which it said it did successful, and also said that the new FAT-32 LBA partition I created was OK.  I then tried to boot into Linux and format it in FAT-32 using GParted, but it never stopped scanning.  I then got HardDrake (from PCLOS) and tried to use that to format it, which it said did not complete successfully.

I'm at work now, but when I get home I will try GParted again a few times.

Wow this is soooo frustrating!!!  

Have any of you ever heard of problems like this?  I guess it's possible I have a bad-drive, but I don't want to throw it away just yet because if it's just some setting that I messed up, I don't want to lose all the money I invested in it (probably about $200 a year ago)...

---

### Post by josephpford on 2007-08-07
> **Inxsible said:**
> Connect your USB drive to the machine and do this.
```
sudo fdisk -l
```Also post the output of ```
gksudo gedit /etc/fstab
```

I will do this when I get home - thanks for your help.

Regards,
Joseph Ford

---

### Post by cwrann on 2007-09-03
If you have not yet found the solution to this yet i read in another post that you need to go into windows with the drive connected and use the safley remove hardware function. After it is reconnected in ubuntu it should work.

---

