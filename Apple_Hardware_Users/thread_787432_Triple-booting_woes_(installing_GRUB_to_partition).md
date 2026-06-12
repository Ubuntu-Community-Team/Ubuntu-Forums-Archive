---
title: "Triple-booting woes (installing GRUB to partition)"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by Aranel on 2008-05-08
I recently wiped my Santa Rosa MacBook (macbook3,1)'s hard disk clean and, consequently, felt that now was a good time to install a Leopard/Hardy/Vista triple-boot on it. But I'm running into a problem: GRUB won't install on the Ubuntu partition. At the very end of the installation, the installer said (to the best of my memory), "grub-install /dev/sda2 failed. This is a fatal error" in a dialog box, and then the installer closed when I clicked OK. When I try to manually run *sudo grub-install /dev/sda2* from the LiveCD, it tells me, "Could not find device for /boot: Not found or not a block device." I can see and mount /dev/sda2 just fine; nothing appears to be out of the ordinary, and Google and forum searches are failing me.

My partition map is as follows:

Partition 1: reserved by EFI (FAT32; 200MB)
Partition 2: Linux / (JFS; 9GB)
Partition 3: Windows Vista (NTFS; 25GB)
Partition 4: shared storage (FAT32; 32GB)
Partition 5: Mac OS X 10.5 (HFS+; 38GB)
Partition 6: Linux swap (swap; 3GB)
Partition 7: Linux /home (JFS; 4.47GB)

The GPT/MBR tables are all synced, rEFIt is behaving nicely (except for not displaying Ubuntu as a boot option :p), GRUB can install to the MBR just fine... but I just can't get it to install to the Ubuntu partition. What's going on here? Any advice/diagnoses/ideas would be greatly appreciated.

Edit: It's probably worth mentioning that I'm trying to install the 64-bit version of Hardy.

---

### Post by cyberdork33 on 2008-05-08
could be that it is JFS.
[https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/14010](https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/14010)

---

### Post by Aranel on 2008-05-09
> **cyberdork33 said:**
> could be that it is JFS.
[https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/14010](https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/14010)

...Aha. I guess I'll go reformat as ext3 and see what happens. Thanks!

---

### Post by Aranel on 2008-05-09
Ubuntu boots fine after reformatting the JFS partitions as ext3, but now Windows won't install. It tells me, "Windows was unable to find a system volume that meets its criteria for installation" when I format the NTFS partition and try to install it there... even though it installed to *that very same partition* yesterday without complaint. I think it has to do with the fact that the Ubuntu partition is flagged as bootable somehow... bah. I shall investigate.

---

### Post by logos34 on 2008-05-09
maybe try deleting the ntfs partition and reformatting it from the Vista installer.

Then again, your signature says it all.

---

### Post by Aranel on 2008-05-09
> **logos34 said:**
> maybe try deleting the ntfs partition and reformatting it from the Vista installer.

Then again, your signature says it all.

I tried that... and after I did, not only did Windows refuse to install, but the partition tables got out of sync, OS X was unable to see the NTFS drive, and Linux became unbootable again.

I just repartitioned from scratch using Disk Utility and am currently reinstalling OS X... again. Yay Microsoft! :roll:

---

### Post by Aranel on 2008-05-09
At long last! Leopard, Hardy, and Vista are booting up fine, the shared-storage partition is recognized by all, and the GPT/MBR tables are in harmony. Here's a little "ten-step plan" to what I did:

1. Boot from the OS X installation DVD. Open Disk Utility, highlight the hard disk, and from the "Partition" menu, create the six partitions of appropriate size. Make them all FAT32, except the one that will contain OS X.

2. Install OS X on the appropriate partition.

3. Install rEFIt and do a cold boot to activate it.

4. Boot from the Vista installation DVD. Format the appropriate FAT32 partition as NTFS and install.

5. When the computer restarts during the installation, don't select the new Windows entry; instead, boot into OS X, eject the Windows DVD, insert the Ubuntu CD, and restart. (The reason we're not booting into Windows just yet is that it'll assign drive letters to all the FAT32 partitions we still have. To avoid that, we need to format them first, which we do in the next step.)

6. Boot from the Ubuntu CD, start the installer, format the appropriate FAT32 partition(s) as ext3 (*not* JFS!) and/or swap, set GRUB to be installed to the correct partition, and install.

7. Reboot once the installation is complete and resync the GPT/MBR tables through rEFIt. At this point, Ubuntu boots fine, but Windows BOOTMGR gives an error that it couldn't find some startup file.

8. Boot from the Windows installation DVD and select the "Repair" option after setting the language/keyboard layout. A screen pops up saying that it has detected a problem. Click "Repair and restart" (or whatever the option says).

9. Select the Windows option from the rEFIt menu, which--hallelujah!--works now.

10. Finish the Windows installation.

There's probably a less convoluted way of doing it, but this one worked for me. Thanks for the help, guys. :)

---

