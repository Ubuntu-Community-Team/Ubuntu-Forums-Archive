---
title: "cant install Xubuntu &quot;Alternate install CD&quot; from USB"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by prot73 on 2008-03-12
hi,

i am trying to install xubuntu from an usb drive on a thinclient pc (no CD).
i dloaded the "alternate install cd" from xubuntu.org and followed this tutorial:
[http://jsco.org/dectop/#installing](http://jsco.org/dectop/#installing)

basically it is so:
   1.  We've already made the USB stick bootable and copied the files onto it.
   2. Don't bother moving the files in /isolinux or in /install into the root directory. Instead, rename the /isolinux directory to /syslinux.
   3. In /syslinux, rename isolinux.cfg and isolinux.bin to syslinux.cfg and syslinux.bin.
   4. Edit syslinux.cfg and replace all instances of "kernel /install" with "kernel ".
   5. Delete the file /dists/stable, create a new directory /dists/stable, and copy the files from /dists/dapper into /dists/stable.
   6. Boot from the flash drive! (If you want ethernet, now would be a good time to make sure you've got the USB ethernet adapter plugged into the decTOP and connected to your network. Autodetection works like a charm on that little guy.)
   7. Go through the default install process up to the point where it asks you about your CD drive. Say "no" to floppies, say "no" to manually selecting a location. Allow this step to fail. Once it has failed, you'll be back at the main menu.
   8. Use Alt-F2 to switch to a different virtual console. Hit enter, then sneakily mount your USB drive at /cdrom using this command: mount -t vfat /dev/sda1 /cdrom. Use Alt-F1 to switch back to the first console where your menu is waiting.
   9. Select the "detect CD-ROM" option again (it should still be highlighted). Everything should proceed smoothly from here, as if you were installing from a CD-ROM.

i have reached step8, but there i have an error:
"mount -t vfat /dev/sda1 /cdrom" says "mounting failed: no such device"

i do have the usb stick as "/dev/sda1" (checked with dmesg).
but looks like there is a problem with vfat, "modprobe vfat" says "module vfat not found"

am i doing something wrong? is there any way i could fix this?

many thx in advance

---

### Post by hyper_ch on 2008-03-12
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by prot73 on 2008-03-12
many thx but it is pretty much the same guide and it does not work.
your link says that instead of my step8 i should do:
"
      mkdir /cdrom /dev/cdroms
      cd /dev/cdroms
      ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
      mount -t vfat /dev/cdroms/cdrom0 /cdrom
"

i get the same error on the mount command: "no such device"
the problem is that i do not have the "vfat" module

---

### Post by prot73 on 2008-03-12
> **hyper_ch said:**
> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

going deeper from your link, it looks like i found an workaround.
the "alternate install cd" does not have vfat in initrd; and i should use the initrd from the desktop iso. 

details here
[http://ubuntuforums.org/showpost.php?p=4303227&postcount=26](http://ubuntuforums.org/showpost.php?p=4303227&postcount=26)
[http://ubuntuforums.org/showpost.php?p=4303227&postcount=27](http://ubuntuforums.org/showpost.php?p=4303227&postcount=27)

i'll give it a try .. thx

---

