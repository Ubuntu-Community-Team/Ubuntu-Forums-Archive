---
title: "i-Mac G3/600 Not booting with Ubuntu Disk"
date: 2008-02-14
forum: Apple PPC Users
---

### Post by kq6up on 2008-02-14
I am trying to load Ubuntu 7.10 on a i-mac g3/600 and the disk does not boot.  OSX can read the disk contents just fine after it starts up.  I am holding down the C key, but the disk just pops out and OSX continues to boot.  I am using a non-mac USB keyboard.  I do not know if this is an issue.

Any suggestions?

Chris

---

### Post by stevejesus on 2008-02-14
Did you make sure and wait fro thing "ding" before you pressed the C Key?  If I remember right, that's how I have always done it.

---

### Post by stevejesus on 2008-02-14
You can also boot the CD from OpenFirmware using CTRL+OPTION+O+F.  This will take you to OF's terminal.

---

### Post by kq6up on 2008-02-14
Is the option button the windows button on a non-mac keyboard?

---

### Post by stevejesus on 2008-02-14
hmmm...  I don't know, but I would try it.

---

### Post by stream303 on 2008-02-14
Try burning the iso at a ridiculously low speed like 1x or 2x..

For a first time install on that machine, I'd probably recommend 7.04, Feisty, and use the "alternate" installer.  If that goes well, an online upgrade to 7.10 might work better.

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

But let's see if a slow-burn can get 7.10 to boot ...

---

### Post by stream303 on 2008-02-14
Oops, forgot - have you tried holdng down the ALT key?

---

### Post by bodycoach2 on 2008-02-14
You'll need to make sure you have at least 128 mb ram. Also, the G3's rarely boot a LiveCD. If you intend on overwriting OSX, use the alternate install disk. Even better, if you can plug up ethernet to that machine, use the minimal CD:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The only disadvantage of the minimal CD for me is that it doesn't have an OEM installation option.

The advantage of the minimal CD is; since it's acquiring installation packages from the repository, once the system is installed, there is rarely any more packages to update. You start off with the latest packages. Also, you can choose any of the desktop environments from the minimal CD installation. I recommend Xubuntu for the G3.

Choose the 32-bit PowerPC. I recommend Fiesty Fawn, as too many people have had difficulty with Gutsy on the G3's.

---

### Post by kq6up on 2008-02-15
This particular box has 500 Mb of RAM so it is not too bad off.

Thanks for the input.  I will give it a shot.

Chris

---

### Post by kq6up on 2008-02-15
I'm starting to think that I need a Mac keyboard and not a generic USB keyboard to get it to boot.  I cannot get into the open fimware, or get it to boot the OSX disk I burned from an image.  The CD mounts fine, and I can brows its contents.  Arrgg!

Thanks,
Chris ](*,)

---

### Post by stream303 on 2008-02-15
Frustrating.  Are you burning the disk as an iso image with OSX disk-utility, or just copying the iso file to the cd?

When you say you can browse the cd, is it the Ubuntu CD?  If it shows only the one iso file, it isn't burned properly.

Hmm... have you tried using a different brand of media?  Or perhaps burning is actually bad on your Mac - can you try burning the image on some other machine at low speed?

Couple of things might help here..

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or it could be that the guys in Cupertino found out what you are trying to do, and aren't too happy about it. :)

---

### Post by linear on 2008-02-15
> **kq6up said:**
> I'm starting to think that I need a Mac keyboard and not a generic USB keyboard to get it to boot.  I cannot get into the open fimware, or get it to boot the OSX disk I burned from an image.

Quite possible - that's one of the things Apple recommends you check (also that keyboard is plugged directly into the Mac, not into a hub).

---

### Post by kq6up on 2008-02-15
No, it is not a single iso file on the disk ;o)  I figured that one out back in 1999 when I first started farting around with Linux. ;o)

I am mac nOOb, but I have been using Linux for a while.

I tried burning it on the mac itself, and on my Ubuntu PC.  I can see all of the files in the CD just fine, so I do not think the mac is having trouble with the CD.  I think it is the third party keyboard.  I have not been able to get into the bios yet.  They keyboard also flakes out when the box goes into sleep mode and restores.  I have to unplug/plug to get it to type again.  I will have to borrow someone's keyboard.

Chris

---

### Post by stream303 on 2008-02-16
New keyboard sounds like the best bet.  Sounds like it doesn't like to wake up.  Maybe we can force it awake...

Hrmm... can you trick it by initially powering up with only the cdrom in the drive, and then attach the keyboard quickly?  I guess you'd have to be fast, but worth a shot if you've got no other option while you wait for the other keyboard...

---

### Post by kq6up on 2008-02-23
It was definatly the the keyboard.  Someone gave me  a mac keyboard and all is good.

Chris

---

