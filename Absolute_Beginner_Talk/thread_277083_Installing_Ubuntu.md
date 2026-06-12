---
title: "Installing Ubuntu"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Matrixs on 2006-10-13
i was going to install and it listed 2 80g hard drives. I am running 2 80g raided as one big drive, i think its raid 2 (160g of space) my question is that if i install this one of the hard drive listed will it wipe out my windows xp. I would like to duel boot xp and Ubuntu, so i dont want to wipe out anything that windows would use. thanks for any input.

---

### Post by pay on 2006-10-14
You can shrink a XP drive then use the freed up space. I'm not entirely sure on how to do that as I've never done it but google should show you how.

---

### Post by BoneKracker on 2006-10-14
Read this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Matrixs on 2006-10-14
thanks that looks like it may help, hope it works. ;)

---

### Post by Matrixs on 2006-10-15
well it didnt work and i follow the install on freed space and formated some of the window areas or something windows or ubuntu would not boot. Anyway iam tring to install just ubuntu on system and i keep getting grub can not install to hd0 error code is below
:neutral: 

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 553, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

---

### Post by BoneKracker on 2006-10-15
Regarding GRUB: If you are trying to dual-boot, then you probably should be using a bootloader (one other than the Windows bootloader, which blows).

Regarding the installer seeing two disks instead of your single RAID device:  The FakeRAID HowTo _does_ say that the easy way probably won't work (i.e., that simply loading dmraid doesn't work and ubiquity fails (which at first glance appears to be what happened to you) in which case you have to follow through with the manual procedures outlined in the howto).  Did you read the whole thing and actually follow the instructions?

Other alternatives to following those instructions. 
a) Get another disk and put Ubuntu on it.
b) Back up Windows, disable RAID in your BIOS, and put it back on a single drive (and put Ubuntu on the other).
c) Back up Windows, disable RAID in your BIOS, repartition each drive in half, reinstall Windows onto the first partition of the first drive, and use the first partion of the second drive for "Documents and Settings", mounting it appropriately -- then install Ubuntu onto the two remaining partitions, configuring them as RAID using (using the Logical Volume Manager built into Linux)
d) Back up Windows, get another drive, install Windows on it.  Then disable RAID in your BIOS, and install Ubuntu on the two original drives, configuring them (or an equal percentage of each) as RAID (using the Logical Volume Manager built into Linux).

---

### Post by Matrixs on 2006-10-15
the windows is not there anymore iam just trying to get the ubuntu to install and i keep getting that error, it gets to like 93% and it trys to install grub and it said that can't install to HD0.

---

### Post by BoneKracker on 2006-10-15
Maybe you didn't get /boot/grub/menu.lst quite correct?

There's a lot of discussion about configuring that file in the howto.

If you think that might be it, you can post it here and I'll take a look at it.

---

### Post by rlozano on 2006-10-15
im not sure if RAID disk are being read by linux (or Ubuntu) as hd0. i believe it considered RAID disk as scsi, so the treatment will be /dev/sdxx. :-k

why not booth from grub first using a floppy or cd? if you know how to grub, then it maybe able to help you install the bootloader properly in your taget disk part. (i can e-mail you the cd iso if you want.)

hope this helps... ](*,)

---

### Post by Matrixs on 2006-10-15
basicly iam doing a new install because when i did the first install it messed up windows so i fdisked it and started to just install ubuntu. but when the install come to installing grub at the last part of the install it come up with cant not install grub on to hd0. the 2 hard drives are showing as 1 big drive as hd0. some reason the grub error on install. you think booting grub first might fix the install. i have no idea about all of this. tring to get it installed so i can can learn more.](*,)

---

### Post by BoneKracker on 2006-10-15
If your still seeing "hdo" related grub errors, then you didn't follow the instructions.

As to "hd0" vs "sd0", that's not right either.

BIOS-dependent "RAID" devices (i.e., the kind built into the motherboard these days) are not seen as "sdx" until after they are mapped to "sdx" by the "device-mapper".  

The complicating factor is that the device-mapper does not get running until after the kernel is loaded and running, so you can't use "sdx" to refer to the devices.

Instead of "/dev/sd0"

The RAID device needs to be referred to as something like: "/dev/mapper/via_hfciifae"

Go back to the HowTo and carefully read the section that talks about configuring the bootloader.

That's just for the bootloader.  Once the device-mapper is engaged, you can refer to it as sd0 or whatever it comes up with.

Don't give up -- you are very close.  It's just getting the right stuff on a couple lines in the menu.lst file!

---

### Post by BoneKracker on 2006-10-15
Oh, and by the way...

Since you removed Windows, you might consider using the RAID capability that comes built into Linux.  That's much less complex to do.

You only need to go this ugly route if you:
a) Have bios-dependent "RAID" controller (a.k.a. FakeRAID, SATARaid) such as provide with some chipsets (e.g. Nvidia, VIA).
b) Are installing Linux onto that RAID array.
c) Can't disable it and use built-in Linux "softRAID" (i.e. LVM), because you wish to keep using the FakeRAID for Windows or some other crap OS that can't do RAID by itself.

---

