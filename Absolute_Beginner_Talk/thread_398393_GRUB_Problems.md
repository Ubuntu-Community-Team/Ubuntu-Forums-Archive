---
title: "GRUB Problems"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Browzilla on 2007-03-31
So I FINALLY got 6.10 installed, turns out I had to reburn it at a slower speed.   Anway.  I finally got Ubuntu installed on a 40g secondary drive, and then rebooted, and got a GRUB error.  Error 21.  The one where it can't find the hard disc, I believe?  

When I installed GRUB, I selected the default config, (hd0).  Could someone tell me what I'm doing wrong, and which hard drive I need to install it on?  

I've got a 40g drive with the Ubuntu install, an 80g with an XP install, and a 500g external fat32.    And I don't want anything on the XP drive compromised or lost.  Should I install to the Ubuntu drive?  Or which?  And, if someone could help me figure out how to change the location, that'd be great.

---

### Post by confused57 on 2007-04-01
> **Browzilla said:**
> So I FINALLY got 6.10 installed, turns out I had to reburn it at a slower speed.   Anway.  I finally got Ubuntu installed on a 40g secondary drive, and then rebooted, and got a GRUB error.  Error 21.  The one where it can't find the hard disc, I believe?  

When I installed GRUB, I selected the default config, (hd0).  Could someone tell me what I'm doing wrong, and which hard drive I need to install it on?  

I've got a 40g drive with the Ubuntu install, an 80g with an XP install, and a 500g external fat32.    And I don't want anything on the XP drive compromised or lost.  Should I install to the Ubuntu drive?  Or which?  And, if someone could help me figure out how to change the location, that'd be great.
Here's a description of grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

The only instance where I've gotten an error 21 was bios related, the IDE controller for the slave drive was set to "off"...all I had to do was reset to "auto".  Is this a recently added drive and the jumper settings on the hard drive are set to "slave" or "cable select"?

You might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Also, what is your hard drive boot order in bios, including your external drive?

---

### Post by Browzilla on 2007-04-01
> 
Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9256    74308657+   7  HPFS/NTFS
/dev/hda3            9257        9725     3767242+  db  CP/M / CTOS / ...

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4676    37559938+  83  Linux
/dev/hdb2            4677        4863     1502077+   5  Extended
/dev/hdb5            4677        4863     1502046   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60613   486873891    c  W95 FAT32 (LBA)
/dev/sda3           60614       60801     1510110    5  Extended
/dev/sda5           60614       60801     1510078+  82  Linux swap / Solaris

That was my fdisk.  

As for boot order, I'd have to check, but I believe it's the XP, then Ubuntu, and I guess the external last.  I haven't tried booting anything off of the external yet, so I'm not all that sure.

---

### Post by confused57 on 2007-04-01
The computer that I had to set the slave drive to "auto" was a Dell, the only way a single hard drive connected to the master controller would boot was to have the slave drive controller set to "off".
I added a second hard drive & had to reset it to "auto"...might want to check this when you're checking your hard drive boot order in bios.

---

### Post by Browzilla on 2007-04-01
So wait.  I've got a Dell Dimension 3000.  Or 2000.  Can't quite make out the first digit from here.  Anyway, in BIOS I get the following under Drive Configuration:
Diskette Drive A: Not Installed

Primary Master Drive: Hard Drive
Primary Slave Drive: Unknown Device
Secondary Master Drive: CD-ROM Device
Secondary Slave Drive: Unknown Device. 

IDE Drive UDMA: On

The unknown devices are when I set them to Auto, otherwise it reads "Off" 

Also, it appears that my secondary drive doesn't appear in my boot order.  According to BIOS, I have Drive C first, then the CD drive.

---

### Post by confused57 on 2007-04-01
> **Browzilla said:**
> So wait.  I've got a Dell Dimension 3000.  Or 2000.  Can't quite make out the first digit from here.  Anyway, in BIOS I get the following under Drive Configuration:
Diskette Drive A: Not Installed

Primary Master Drive: Hard Drive
Primary Slave Drive: Unknown Device
Secondary Master Drive: CD-ROM Device
Secondary Slave Drive: Unknown Device. 

IDE Drive UDMA: On

The unknown devices are when I set them to Auto, otherwise it reads "Off" 

Also, it appears that my secondary drive doesn't appear in my boot order.  According to BIOS, I have Drive C first, then the CD drive.
OK, on my Dell Dimension 4550 there is no way to change to hard drive boot order, it always boots first to the Master drive on the IDE1 controller...I believe on this controller the master & slave hard drives are designated hd0 & hd1, respectively.  You can confirm that your hd1 is set to "auto" and you're sure that the jumper settings on the slave hard drive are set to "slave" or "cable select".

To dual boot Ubuntu & Windows on separate drives, I had to install Ubuntu to my new hard drive connected as master on IDE#1...after I installed Ubuntu, I then reconnected my current Window's drive as slave & added an entry in grub to boot Windows.   See this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

If you have access to another computer you might want to download the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
you can use the SGD to boot Windows or Ubuntu...also, you can use it to restore your Window's drive mbr, so that  can boot Window's using Window's IPL code.

Once you can boot Windows independently of grub, then you might want to consider installing Ubuntu the way I suggested, i.e. Ubuntu on master & Windows on slave...again, you have to make sure your jumper is set correctly on your hard drives.

If you don't have access to another computer, you might want to connect your current Ubuntu drive as master and reinstall Ubuntu...once you're able to boot Ubuntu, then you can make a copy of the Super Grub Disk...Windows should also boot from grub even if you haven't restored Window's IPL code to the mbr.

Are you getting a grub menu booting with your current setup, are you getting options to boot Ubuntu or Windows?

---

### Post by Browzilla on 2007-04-01
Hardware support is where my knowledge of computers is lacking greatly, so I'm not all too sure about this.  I found the 40g sitting in an old computer and installed it about a two weeks ago.  There were a ton of the grey long hard drive cables (IDE, I believe?) laying around, so I looked through those.  What I have my drives hooked up through is one cable, with the one end in the motherboard, and then the rest of the cable has two connections, the first of which is labeled with a 1 or A or something, and the other one with a 2/B.  A is plugged into my Windows drive; B goes into Ubuntu.  And, if it matters, the external is a USB 2.0.  There's another slot right next to where they're connected which I've been informed is where jumpers go, but I was also informed that the should work without it, so I left those alone.  

As for the last question, GRUB dies before even seeing a menu.  If I let it boot normally off the drive, it goes directly to a screen that shows error 21.  To get anywhere, I have to use the liveCD from my F12 boot menu.  

I could try the Super Grub Disk I suppose, I've got about 5 other computers laying around..
To use that, I'd burn the ISO then boot from the cd to load a boot menu?

---

### Post by confused57 on 2007-04-01
> **Browzilla said:**
> Hardware support is where my knowledge of computers is lacking greatly, so I'm not all too sure about this.  I found the 40g sitting in an old computer and installed it about a two weeks ago.  There were a ton of the grey long hard drive cables (IDE, I believe?) laying around, so I looked through those.  What I have my drives hooked up through is one cable, with the one end in the motherboard, and then the rest of the cable has two connections, the first of which is labeled with a 1 or A or something, and the other one with a 2/B.  A is plugged into my Windows drive; B goes into Ubuntu.  And, if it matters, the external is a USB 2.0.  There's another slot right next to where they're connected which I've been informed is where jumpers go, but I was also informed that the should work without it, so I left those alone.  

As for the last question, GRUB dies before even seeing a menu.  If I let it boot normally off the drive, it goes directly to a screen that shows error 21.  To get anywhere, I have to use the liveCD from my F12 boot menu.  

I could try the Super Grub Disk I suppose, I've got about 5 other computers laying around..
To use that, I'd burn the ISO then boot from the cd to load a boot menu?

Sounds like you have the hard drives connected to the IDE cables correctly, but I believe you need to have the jumper set correctly on both drives...I assume your Window's drive jumper is correct since you were able to boot  Windows before installing Ubuntu.
A hard drive jumper is a small piece of plastic that attaches to the back of your hard drive & connects to pins according to whether you have the drive as master or slave.  There should be a diagram on the top of the hard drive instructing where to install the jumper for master or slave.
This explains a little about jumpers:
[http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm](http://www.pcguide.com/byop/byop_SettingHardDriveJumpers.htm)

---

### Post by Browzilla on 2007-04-01
And so...I want which drive as the slave?  The Ubuntu?  Or does it nor matter, just as long as one is, and GRUB knows which is which?

---

### Post by 3rr0r on 2007-04-01
Try slave or auto

---

### Post by Browzilla on 2007-04-01
And after I set that?

---

### Post by confused57 on 2007-04-01
> **Browzilla said:**
> And so...I want which drive as the slave?  The Ubuntu?  Or does it nor matter, just as long as one is, and GRUB knows which is which?
  If your Dell is like mine, grub will need to be on the master drive, whether Ubuntu or Windows is installed.  What you can do is try to install grub to your Ubuntu drive mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
From this link, boot the live cd open a terminal & enter:
```
sudo grub
find /boot/grub/stage1
```
which may return something like
root (hd1,0)
if it does, then enter:
```
root (hd1,0)
setup (hd1)
quit
```

if grub is successfully installed to (hd1),turn it off & open your pc, connect the master end of the IDE cable to the Ubuntu drive(jumper will need to master), leave the slave end disconnected...boot your pc, go into bios, turn the IDE#1 controller slave drive to "off", then finish booting your pc.
If you get a grub menu, highlight your Ubuntu entry, press "e", change root to (hd0,0), then press "b" to boot.

If the attempt to install grub to your Ubuntu drive mbr fails at the beginning, you may want to try  reinstalling Ubuntu with just the Ubuntu drive connected as master, Window's drive disconnected.

---

