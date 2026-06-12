---
title: "Dual Booting Ubuntu from external - need help getting it to Boot"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by pdoran on 2007-12-28
I know, another beginner trying to dual boot. 
I've looked around for help, and I've pretty much been following this:
[http://ubuntuforums.org/showthread.php?t=421962]("http://ubuntuforums.org/showthread.php?t=421962")

Here's what I'm trying to do:
Laptop internal hard drive boots Windows XP
160gb external hard drive boots Feisty (the laptop can boot from USB)
The external hard drive also contains about 40gb of random files
When the external is connected to the laptop, it boots Ubuntu without prompt. When it is disconnected, it boots Windows without prompt.

Here's what I've done so far:
Used the simplest installation method to install Feisty to the external (given 65gb partition, my 40gb of random files are still there)
Found that my laptop required the external to be on so I could boot windows (with prompt)
Used Super GRUB disk to restore the MRB so I can boot Windows (without prompt)
Tried to install GRUB to the external partition using the sgd.
Changed the boot order to boot from usb before booting from internal HDD

To conclude:
XP is on my laptop.
Feisty is on my external
I am booting from USB first

With that, when I boot my laptop, it gets to a black screen with a single '_' blinking.

When I change to booting from internal first, my laptop boots XP as expected.

I'm not exactly sure what the problem is because I can use sgb to boot Ubuntu from the external HDD. I want to say it has something to do with GRUB, but what do I know? Clearly nothing.

Can anyone help me solve this problem?

---

### Post by blueridgedog on 2007-12-28
My guess is now that you have restored the mbr, Windows boots fine, and since Ubuntu was installed with the internal as the first boot device, I would wager that the boot loader was put on the internal drive (which has since been wiped out).

Two things come to mind to try:

1.  Install Ubuntu onto the external after having removed (physically) the internal.  It will install the boot loader on the external and it should function as a stand alone drive.  It should also take precedence when plugged in, due to the bios changes you made.

2.  Alternatively, try this tool/site:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by pdoran on 2007-12-28
Are you sure I have to reinstall Ubuntu? The thread I've been following suggests that I should be able to install GRUB on the external hard drive from the Super GRUB disk.

---

### Post by dstew on 2007-12-28
Yes, I think you can install grub onto the external drive, if your BIOS can boot the drive. You will need to install grub onto the external drive. With the external drive plugged in, using the supergrub disk, you should be able to install it. You should install grub to the MBR of the external disk, *not* to the first partition. In otherwords, assuming your external disk is (hd0) to grub, the commands (on a grub command line) would be```
find /boot/grub/stage1
```Use the result as the root:```
root (hd0,0)
setup (hd0)
quit
```You might be getting in trouble, though, if the BIOS changes the disk enumerations depending on the boot order, or whether a CD is in. So, when the supergrub disk is in, the external drive might be (hd1), but when it is not in it is (hd0). Some BIOSes do this, much to grub's consternation. Usually you can figure it out with some trial and error.

---

### Post by logos34 on 2007-12-28
I agree with Blueridgedog up to his first recommendation--you don't need to reinstall.  

> Tried to install GRUB to the external partition using the sgd.

Maybe it installed grub to the bootsector of the root partition rather than the mbr of the USB?  And you have to change /boot/grub/menu.lst because now that you are changing the Bios boot directly to grub on the usb drive, it is seen as (hd0).  So you have to change the 'root' lines (and 'groot') in menu.lst to (hd**0**,?). So for instance if root is sda1, then **(hd0,0) **instead of (hd1,0)

Boot from the live cd, click on root partition in Places>computer to mount, go to menu.lst and change it:

gksudo gedit /media/disk/boot/grub/menu.lst

Then [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351"):

sudo grub

> root (hd0,0) --> or whatever root # is 
> setup (hd0)
> quit

Edit: looks like dcstew beat me to it

---

### Post by pdoran on 2007-12-28
Thank you guys for helping me. With DStew's suggestion I have gotten the grub menu to show up, but I cannot boot anything from it.

When trying to boot any of the Ubuntu 
```

Error 17: Cannot mount selected partition
Press any key to continue...

```

When trying to boot Windows XP from the GRUB menu
```

Starting Up...
GRUB loading Stage 2...

```
and then it brings me back to the GRUB menu

I'm guessing this has to do with menu.lst but I'm not sure what to do with it.
Suggestions?

---

### Post by logos34 on 2007-12-28
> **pdoran said:**
> I'm guessing this has to do with menu.lst but I'm not sure what to do with it.
Suggestions?

Why don't you try reading the suggestions people make?

---

### Post by dstew on 2007-12-28
You are right. The error messages are coming from grub stage 2. You know this because they have the brief explanations.

This means that grub is basically installed correctly. All you need to to is fix up your menu.lst file. To make sure we edit it correctly, post the output of these commands:```
sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst
```

EDIT: Sorry I forgot you do not have your system bootable yet. To edit your /boot/grub/menu.lst, you will need to boot a LiveCD Ubuntu system. After that, do **sudo fdisk -l** and post that result. The other commands will require us to mount the disk. I'll be able to help you with that.

---

### Post by pdoran on 2007-12-28
removed

---

### Post by meierfra on 2007-12-28
I wrote a howto (see DualTwo in my signature)  for this kind of problem.

It assumes that you can boot into ubuntu. So it no longer applies directly.

But it also can be done from the LiveCD. Except for  Step 1 (editing menu.lst).  Use  the   method from Logos34 first post instead.

---

### Post by dstew on 2007-12-28
From the looks of your menu.lst and fdisk outputs, it seems that your Ubuntu root should be (hd1,1) and your Windows root should be (hd0,1). So, the Windows item seems to be correct, but not the Ubuntu entries. groot (hd1,1) seems to be the correct choice also. If it still doesn't boot with these entries, it may be a problem with changing enumerations.

Also, how did you get these commands to work? Did you boot a LiveCD? Did you boot your Ubuntu installation from the Super Grub disk?

Last of all -- a CP/M partition? That's a real throwback!

---

### Post by meierfra on 2007-12-28
> It seems that your Ubuntu root should be (hd1,1) and your Windows root should be (hd0,1). So, the Windows item seems to be correct, but not the Ubuntu entries. groot (hd1,1)

That is wrong. pdoran will be booting from the external drive to   get  ubuntu.  Grub (at boot-up)  always sees the booting drive as  (hd0).  That's why Logos34  told pdoran to change the  "groot" and "root" lines.

---

### Post by blueridgedog on 2007-12-28
I agree with the others who stated a reinstall is not needed.  If you can boot off the live CD and install grub to the USB drive that would have the same effect.

I was suggesting a reinstall as a shortcut to getting the install to do the work for you given that my read of your problem was that you had not spent a great deal of time setting up Ubuntu and thinking that a reinstall without your internal HD would in theory make things work.  If you are trying to save the current install, putting grub in by hand is the trick.

---

### Post by dstew on 2007-12-28
Meierfra said:> Grub (at boot-up) always sees the booting drive as (hd0).Are you sure about this? I thought that the grub boot loader just used the BIOS drive table, that the drive number depended on how the BIOS enumerated the drives. I don't know a lot about BIOSes, but is it true that all BIOS make the boot drive to be drive #0 also? If so, that would explain a lot of grub problems that arise when changing boot order. I am sure some BIOSes do this, but is it a universal rule? Thanks.

---

### Post by pdoran on 2007-12-28
Thank you dstew, logos, meierfra, and  blueridge for replying to my problem. I appreciate your help. I was able to fix what I had done and then was able to use meierfra's DualTwo guide by booting from partition with SGD and then just following the guide. I wish I had known about that sooner; it would have saved me several hours of painful work.

Once again, thank you everybody.

---

### Post by blueridgedog on 2007-12-28
meierfra's HOWTO is pretty clear and well written.  Glad you have it working.  The big picture view is to get a boot loader onto each drive, and realizing that when the external drive is plugged in, with the bios set correctly, is enumerated first.

---

