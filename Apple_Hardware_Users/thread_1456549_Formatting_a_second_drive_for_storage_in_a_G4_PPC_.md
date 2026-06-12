---
title: "Formatting a second drive for storage in a G4 PPC rinning 9.10?"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by sastusbulbas on 2010-04-17
Hi,

I have a second 80gb drive and can't seem to get it formatted with disk utility, what label and type should I put?

Putting Linux Ext 4 freezing up the system. I have the jumper in the part labelled as slave.

Would like to have this set up as a second drive for storage.

---

### Post by tom4everitt on 2010-04-18
That sounds way to familiar. Disk utility is pretty unstable (I assume you're talking about the osx app), especially when doing non-standard stuff such as creating a linux partition. 

Any reason you don't want to do the partitioning in linux?

---

### Post by sastusbulbas on 2010-04-19
I only have Linux, Ubuntu 9.10 on the Mac, loaded on a 20gb drive. I added a second 80gb drive and though it gave me the option to delete I can't seem to get it running as a second storage drive, probably something simple, but then again Ubuntu can't seem to get anything running on a PPC these days.

---

### Post by tom4everitt on 2010-04-19
oh, I think i completely misunderstood you. I thought you meant disk utility in mac, in linux most people call disk utility for gparted.

---

### Post by tgalati4 on 2010-04-19
Is this a laptop (i.e. powerbook G4)?  If so, then the USB drive may not be getting enough power.  Try using an external power supply for the drive.

---

### Post by sastusbulbas on 2010-04-20
Hi,

It's not a laptop, but a desktop PPC.

This one,
[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html)

OSX 10.1 has no problems with any of the hardware, just Ubuntu or me being a noob. 

I have the second drive wired as slave, it does not show up on the computer, Ubuntu Disc Utility can see it and erase it, when I try to format it as Linux Ext 4 the system freezes, mouse pointer does not move etc.

---

### Post by tgalati4 on 2010-04-20
That G4 is pretty slow.  Try to format it in ext3 and move on.  Don't waste your time trying to get a little more filesystem performance (with ext4) when the rest of the computer is slow.

---

### Post by linuxopjemac on 2010-04-21
> That G4 is pretty slow. Try to format it in ext3 and move on. Don't waste your time trying to get a little more filesystem performance (with ext4) when the rest of the computer is slow.

I run ext4 on a PowerBook G3/400 just fine.

---

### Post by shawnhcorey on 2010-04-21
> **sastusbulbas said:**
> Hi,

It's not a laptop, but a desktop PPC.

This one,
[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html)

OSX 10.1 has no problems with any of the hardware, just Ubuntu or me being a noob. 

I have the second drive wired as slave, it does not show up on the computer, Ubuntu Disc Utility can see it and erase it, when I try to format it as Linux Ext 4 the system freezes, mouse pointer does not move etc.

Is it listed in /dev?
```
sudo ls -l /dev/hd*
```

Can fdisk see it?
```
sudo fdisk -l
```

---

### Post by linuxopjemac on 2010-04-21
> though it gave me the option to delete I can't seem to get it running

it seems like gparted saw the drive....

---

### Post by oswaldkelso on 2010-04-23
on PPC it's ```
mac-fdisk -l 
```to list the drives. If that fails install parted and try ```
parted -l
```  All as root or with sudo on Ubuntu

---

### Post by sastusbulbas on 2010-05-01
Still not solved this, but then again I am a complete newb with not a lot of free time.

---

### Post by linuxopjemac on 2010-05-02
try gparted and change the device to your extra device (GParted -> Devices -> tick your device
```
sudo gparted
```

BE CAREFUL NOT TO NUKE YOUR HD !!!

---

