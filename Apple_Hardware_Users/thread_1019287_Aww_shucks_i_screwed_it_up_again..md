---
title: "Aww shucks i screwed it up again."
date: 2008-12-23
forum: Apple Hardware Users
---

### Post by Zahlerstreik on 2008-12-23
So,

I've got myself a 320gb hdd with osx on the first 20gb and refit installed on it. ~260gb windows vista. the last 40gb are free. I slapped in the ubuntu 8.10 x64 disk, installed to that single partition with swapfile instaead of swapdrive. Now, my refit only shows linux and macos...I already tried putting an entry in  menu.lst:

title          Windows Vista Ultimate
root           (hd0,2)
makeactive
chainloader     +1

to no avail. this will not load. please note that efi+macos = two partitions, so hd0,2 should be my third partition.

=I'm pretty sure the partition is still there (as the partition table shows it) but I have no clue how to load windows again!

any help or ideas?

p.s. i loaded my windows install disk but it won't run a repair, it just errors before doing anything.

---

### Post by lat2005 on 2008-12-23
When you go to the ubuntu does windows show up on grub as one of the options?

Did you install grub on the same partition as ubuntu? On mine I installed ubuntu (the root /   ) on /dev/sda3 and in the advanced options in the installation (the last screen) I chose to install grub on /dev/sda3 also.

Did windows showed up before you installed ubuntu and disappeared afterwards?

---

### Post by davidshere on 2008-12-23
Windows must run from the first partition, partition 0.

---

### Post by Zahlerstreik on 2008-12-23
> **davidshere said:**
> Windows must run from the first partition, partition 0.

Windows is in fact installed on the third partition. Would grub see it as hd0,0 ? Grub is installed on /dev/sda4 which is where my entire filesystem is mounted.

---

### Post by cyberdork33 on 2008-12-24
> **davidshere said:**
> Windows must run from the first partition, partition 0.
That is incorrect. It actually prefers to be the 4th partition.

I would guess that the likely issue is that when you installed Ubuntu, you overwrote the windows bootloader with grub, thus, you need to replace it. You can start the Windows Disc into the recovery console and use the FIXMBR command to replace it. This will likely overwrite grub now, you you will need to reinstall it to the Ubuntu partition. See [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Also, editing the menu.lst file would make windows show up in the GRUB menu, not refit.

---

### Post by hijk155 on 2008-12-24
[img]http://www.majiang168.com/sd/sd.jpg[/img][China slim Usb Flash Drives Manufacturer](http://www.chinausbflashdrives.com/slim-usb-flash-drives.html)[China finger print Usb Flash Drives Manufacturer](http://www.chinausbflashdrives.com/finger-print-usb-drives.html)[China wristband Usb Flash Drives Manufacturer](http://www.chinausbflashdrives.com/wristband-usb-flash-drives.html)[China capless Usb Flash Drives Manufacturer](http://www.chinausbflashdrives.com/capless-usb-flash-drives.html)[China Lanyards Usb Flash Drives Manufacturer](http://www.chinausbflashdrives.com/Lanyards-usb-flash-drives.html)

---

