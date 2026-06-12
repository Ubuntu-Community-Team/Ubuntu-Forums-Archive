---
title: "Installtion Problem"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Disposable Arts on 2006-11-21
Since i was skeptical about installing GRUB on my first Hd which has XP on it, i decided to use the method shown here [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)  by member "Gn2"
Which was to disconnect the drive with XP on it (master) and install Ubuntu on the slave which would keep GRUB on the slave and far from the master's MBR.

I proceeded to manually partition the drive in which 15GBS was given to the root, and 1GB for the swap file partition....it then showed me where it was going to install grub which was HD0...i decided that since the goal was to keep it on the slave, i changed the location to HD3 which is really the partition i did for the root on the slave drive.....during the actual installation process, i then got an error when it was installing GRUB....i suspect that came from me changing the the location for GRUB to be installed...any help to correct this would be appreciated.

edit- should also add that i'm a bit confused at the "prepare mounts" part of the installation, can someone also explain that?

---

### Post by Ecthelion on 2006-11-21
Isn't it so that grub should be installed at the start of the disk?
In the mbr or in a separate partition mounted as /boot?

I'm no expert but that's what I was thinking...

Maybe it does help....

---

### Post by bulldog on 2006-11-21
If you disconnect your first hard drive (hd0) than it looks to me that your slave drive will be (hd0) because it's the only drive which is connected.

Isn't that difficult to figure out I think :D 
Grub can't guess you have more than one hdd.

---

### Post by LLRNR on 2006-11-21
Hi there ! At my first install I was in the same situation as you are, I had 2 HDDs, the master being with XP and the slave with Ubuntu. (ah well until the second HDD crashed)

The point is to let GRUB be installed on the first HDD. Each HDD has its own MBR as you know but the only "active" MBR is in the master HDD.

You don't have to worry about rewriting the MBR of the HDD with Windows since GRUB (the bootloader Ubuntu uses) automatically recognises the OS's installed. Yes, I think it would be a problem if GRUB was to overwrite another bootloader called LiLo which is used by othere Linux distros, I really don't know anything about that bootloader); at any case, there's actually no problem at all (provided you don't have another Linux distro installed on that HDD which uses by default another bootloader - LiLo - different than GRUB; there is a workaround for this too but I'm not familiar with it). 

It's also easy to recover the MBR just as it was before installing Ubuntu (simply boot from the XP install CD, get in recovery console and type "fixmbr", it's as simple as that).

So I'd suggest you re-plug the master HDD and let GRUB installed on hd0, by default.

If you let your master HDD unplugged and install Ubuntu on the second, with the GRUB in its MBR... well... I think you won't be able to boot in Ubuntu after you reconnect your master HDD. ;)

---

### Post by bulldog on 2006-11-21
> **LLRNR said:**
> Hi there ! At my first install I was in the same situation as you are, I had 2 HDDs, the master being with XP and the slave with Ubuntu. (ah well until the second HDD crashed)

The point is to let GRUB be installed on the first HDD. Each HDD has its own MBR as you know but the only "active" MBR is in the master HDD.

You don't have to worry about rewriting the MBR of the HDD with Windows since GRUB (the bootloader Ubuntu uses) automatically recognises the OS's installed. Yes, I think it would be a problem if GRUB was to overwrite another bootloader called LiLo which is used by othere Linux distros, I really don't know anything about that bootloader); at any case, there's actually no problem at all (provided you don't have another Linux distro installed on that HDD which uses by default another bootloader - LiLo - different than GRUB; there is a workaround for this too but I'm not familiar with it). 

It's also easy to recover the MBR just as it was before installing Ubuntu (simply boot from the XP install CD, get in recovery console and type "fixmbr", it's as simple as that).

So I'd suggest you re-plug the master HDD and let GRUB installed on hd0, by default.

If you let your master HDD unplugged and install Ubuntu on the second, with the GRUB in its MBR... well... I think you won't be able to boot in Ubuntu after you reconnect your master HDD. ;)

Well, yes and no
Most modern computers have the possibility to choose from which hdd you want to boot.
So he can select the second hdd and boot ubuntu with GRUB.
This isn't the most comfortable way to do.
Make your Ubuntu drive the master and the windows slave.
Then add the windows boot to the menu.lst and map the two hdd's
Now you start with grub and can choose to boot ubuntu or windows.
If something should happen with grub,you always can boot windows from it's own bootloader by selecting this hdd as master bootdevice.
To add windows to your menu.lst and the mapping thing if you're interested,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```
Because you disconnect the windows hdd you have to add your windows partition's manually to fstab if you want to use them in Ubuntu.

---

### Post by LLRNR on 2006-11-21
> **bulldog said:**
> Well, yes and no
Most modern computers have the possibility to choose from which hdd you want to boot.


Alright, you have a point, Bulldog... I started with the stupid assumption that there are no smart computers in this world, I just thought of *mine* and figured out how I'd do it. :D Thanks for noticing and suggesting another way to do it.

---

