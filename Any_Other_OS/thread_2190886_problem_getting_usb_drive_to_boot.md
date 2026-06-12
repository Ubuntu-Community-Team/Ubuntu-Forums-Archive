---
title: "problem getting usb drive to boot"
date: 2013-11-29
forum: Any Other OS
---

### Post by penguin128 on 2013-11-29
running  12.04  Ihave a maxtor 100g usb drive, downloaded a mageia3 iso instalation dvd ( sorry just thought I would look at it)  used dd to "burn" image to usb drive,  it worked, changed bios to boot usb and when it comes up it is just a black screen with a curser in top left hand corner,  the isb drive is formatted to fat32 ,  any ideas? what else I can check? change? thnx in advance for any help';;;;;;;;

---

### Post by heir4c on 2013-11-30
Use a usb-stick to boot up with, not a usb-drive. (I never try it with a usb-drive, but if it will work use the following):
Use Multisystem or Unetbootin to make the live-usb, not 'dd'.
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
Unetbootin: you install it via UbuntuSoftwareCenter.

---

### Post by oldfred on 2013-11-30
Moved to otherOS since not Ubuntu.

What video card. With Ubuntu I have to add nomodeset with all boots of live installers or first boot after install. Once I install proprietary nVidia driver then I do not need nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Never dd to another larger drive. You just erased the entire drive as you overwrote the first 700MB of the drive including old partition table. dd is ok if a smaller flash drive that you are ok with totally overwriting, but I prefer any of the other methods as dd is dangerous if you do not understand consequences. 

      
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by penguin128 on 2013-11-30
Thnx for the help,  using the usb ONLY for additional distros,

---

### Post by penguin128 on 2013-12-01
Gheez do I feel idiotic,  what I tried worked only  when using  dd  NEVER NEVER put a number behind the of= drive,,,  redid the dd and rebooted to iso and up she came,,,
Thnx to all who replied

---

### Post by oldfred on 2013-12-01
If you have a hard drive or larger flash drive and want to boot a variety of ISOs, you can just install grub to device and copy as many ISO as will fit. Most ISO now will boot with grub2's loopmount, a few will not.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

On a couple of my larger flash drives I have a full install of Ubuntu as a backup way to boot and then several repair ISO, gparted, partedmagic, Boot-Repair Remix, other Ubuntu etc that I can also boot from grub with loopmount.

---

