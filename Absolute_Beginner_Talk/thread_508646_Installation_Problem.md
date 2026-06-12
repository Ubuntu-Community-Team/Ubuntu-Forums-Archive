---
title: "Installation Problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by rkeslar on 2007-07-24
Last night when I went to install Ubuntu, I installed it on a usb hard disk. Now I get a Grub error 21, which I now realize means that it can't find the disk. This makes sense to me since the disk is a usb disk and isn't recognized by the bios. The problem though is that Ubuntu won't load, but neither will ms windows load. Is there a way I can remove the grub loader so that ms windows boots, and so that I can install Ubuntu on the IDE drive?

Thanks

---

### Post by FleetAdmiral74 on 2007-07-24
If you still have your Windows CD, you can boot that into the recovery/repair mode, and there is a command, something like fixmrb, that will restore the MBR so Windows can boot. Won't fix your Ub problem, but its a temp solution.

---

### Post by Rocket2DMn on 2007-07-24
that's "fixmbr" - fixes master boot record.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true) in case you care.
If you want to try and boot from the USB drive, you will probably have to set the boot order in your BIOS to look at USB before the hard disk since a lot of computers don't load the USB that early in the boot process.

---

### Post by ajgreeny on 2007-07-24
Yes.  As the last post says, you need to set your USB as the first boot device in BIOS and the disk with windows as the second boot device.  Leave the windows MBR on the hard disk and put grub on the USB.
Now when you boot with the USB connected, you will go to grub and can chose which to boot, but when the USB is not connected you will go to the hard disk and windows will boot from the MBR there.

---

### Post by rkeslar on 2007-07-24
How do you get into recovery/repair mode in windows? Do you have to press F4 or something like that?

---

### Post by nitro_n2o on 2007-07-24
> **rkeslar said:**
> How do you get into recovery/repair mode in windows? Do you have to press F4 or something like that?
It's not at the top of my head now, but if you boot from the windows setup CD it'll prompt you for the recovery mode. It'll say something like press 'r' to go to recovery mode or something like that 

hope that helps

---

### Post by rkeslar on 2007-07-24
Oh ok thanks for your help

---

