---
title: "SYSTEM BOOT FAILURE when booting from FreeDOS boot disk."
date: 2016-04-07
forum: Any Other OS
---

### Post by cobalt2 on 2016-04-07
I installed FreeDOS to the flash drive using Unetbootin.
When attempting to boot from the FreeDOS boot disk, I encountered the error: 

SYSTEM BOOT FAILURE! 

Insert System Disk, then press ENTER. 

Why is this happening?

---

### Post by QIII on 2016-04-07
Moved to Any Other OS.

---

### Post by cobalt2 on 2016-04-08
I don't think it's fair to shunt my post to an obscure area of your site, where it is has absolutely no visibility. As I created this boot disk in order to flash the BIOS, I shall post a new thread in Hardware.

---

### Post by oldfred on 2016-04-08
Is this a new UEFI system? And then are you booting in BIOS/CSM/Legacy mode?

Or boot loader did not get installed correctly to MBR of flash drive.

This will show MBR details, if you run report with flash drive plugged in.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by oldfred on 2016-04-08
Do not create duplicate threads.
You can bump once every 12 hours so it is in top of new posts search, which many of us use.

Not directly an Ubuntu related post.

---

### Post by cobalt2 on 2016-04-08
Hello oldfred.

Thank you for *finally* responding to my inquiry.

Actually my inquiry is Ubuntu related since I used Ubuntu based programs to create the boot disc. Obviously if I wasn't an Ubuntu user, I wouldn't be asking for help on this forum.

I didn't know that posting duplicate threads under different topics was against the rules. 

I'm using the BIOS, and need to boot into DOS in order to run a Windows based batch file, to flash the BIOS.

The Ubuntu pastebin URL is [http://paste.ubuntu.com/15700405/](http://paste.ubuntu.com/15700405/).

---

### Post by oldfred on 2016-04-08
It shows syslinux installed to the MBR.
Your system seems to be one that promotes the flash drive to sda. That often causes issues, so be sure to keep track of which drive is which. Grub normally defaults to install to sda, and that would overwrite a boot loader on the flash drive.

But issue may just be that you do not show a boot flag on sda1 or the FAT32 partition on the flash drive.
Syslinux is a Windows type boot loader that has to see a boot flag to find more boot code in partition boot sector and know which partition has that code.
Grub does not use a boot flag, so Linux systems may work without one.

Use gparted and add a boot flag to the flash drive.

---

### Post by cobalt2 on 2016-04-10
I added the boot flag. 

Now when booting from the drive, I'm getting:

> 
SYSLINUX 6.03....
Boot Error.


---

### Post by oldfred on 2016-04-10
Then without boot flag, syslinux probably did not install correctly.
Although flash drive does show syslinux in PBR.

>    Boot sector info:  Syslinux looks at sector 98940 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.

---

