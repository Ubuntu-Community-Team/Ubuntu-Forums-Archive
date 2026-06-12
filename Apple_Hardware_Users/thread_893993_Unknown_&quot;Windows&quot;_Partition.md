---
title: "Unknown &quot;Windows&quot; Partition"
date: 2008-08-18
forum: Apple Hardware Users
---

### Post by rrm74001 on 2008-08-18
I just installed Kubuntu 8.04 on to an external USB drive.  The installation was successful.  I restarted my computer, and of course, it did not show up in the boot menu when I help down the option key at startup.  So I installed the EFI extension called rEFIt onto a seperate USB thumb drive (I did not want to install it on my internal hard drive).  I restarted my computer once again and held down the option, and the USB drive with rEFIt showed up!  I booted from it and it displayed the rEFIt boot menu, and it even showed my USB hard drive with Kubuntu 8.04 as a bootable drive!  So I attempted to boot from it and it displayed this message:

```
no bootable devices
```

I followed the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

I booted the rEFIt via USB once again and told it to sync the partitions.  I restarted my computer once again and now a "Windows" hard drive is appearing in the Apple EFI (not rEFIt) menu, even though I have all USB device unplugged, and I only have Mac OS X installed on the internal hard drive.  I know it is not referring to my USB hard drive with Kubuntu 8.04 because it also appears in the rEFIt boot menu.  If I attempt to boot from the "Windows" drive, it says:

```
Missing operating system
```

I am not sure where it is getting it because it does not appear as if there are any more partitions on my internal hard drive than normal.  Partition Inspector reports:

```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    488134983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    488134983  af  Mac OS X HFS+

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active
```

Why is that "Windows" Disk appearing in the Apple EFI (not rEFIt) menu, and how do I get rid of it.  (The "Windows" drive actually appears in BOTH the Apple EFI menu and rEFIt menu.)

Also, Kubuntu 8.04 still will not boot at all, even though I synced the partitions.  It also says:

```
Missing operating system
```

Thanks for you help!

---

### Post by cyberdork33 on 2008-08-19
First, booting from USB will not work. Sorry. Even if you make it a bootable device, and it shows up in refit (or the Apple bootloader, which are really the same, just a different interface), it will fail with a message about legacy operating systems on USB devices.

Reference:

As linked in the FAQ at the top of the forum:
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

More recent discussion:
[http://ubuntuforums.org/showthread.php?t=867808](http://ubuntuforums.org/showthread.php?t=867808)

If you want to persue this further, I suggest atempting to use something like syslinux.

Second. installing refit on your mac is completely safe and reversible. It does not alter your firmware or anything crazy like that, it only copies some files to /efi/refit on your OSX partition and blesses the executable. Booting it from a USB stick is necessary. Removal instructions are here:
[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

Lastly, I think that the Windows Icon appears because you sunced the partitions on your internal hard drive. This created an MBR partition table on the drive that wasn't there before (and isn't needed). Unfortunately, the refit partition tool is limited to syncing only the primary master hard drive (i.e. your internal drive). The good news is that in Ubuntu you can install "gptsync" for which I think you can specify the device you want to sync (Actually, I think gptsync is just the refit code ported to linux).

If you want to remove the Windows icon, I think that your best bet is to boot the ubuntu livecd and use the fdisk tool to remove the partitions (fdisk can only access the MBR table, not your GPT).

---

### Post by rrm74001 on 2008-08-19
What partition exactly am I sipposed to delete?  If I go to Disk Utility, it only shows one partition, and it is for the "Macintosh HD".  See Screenshot:

[img]http://img124.imageshack.us/img124/3562/picture1zb0.png[/img]

If I go to the Startup Disk Preference Pane, it also only shows one partition, and it is for the "Macintosh HD".  See Screenshot:

[img]http://img230.imageshack.us/img230/3460/picture2dc6.png[/img]

Finally, if I type into the Terminal "diskutil list", it returns this:

[img]http://img230.imageshack.us/img230/4671/picture3sd0.png[/img]

The above image looks normal to me.

The EFI boot menu seems to be the only thing that can see this "Windows" drive.

> This created an MBR partition table on the drive that wasn't there before (and isn't needed)

I think you are correct.  However, only the EFI boot menu can see these partitions.

```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    488134983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    488134983  af  Mac OS X HFS+

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active
```

I booted into my Live Kubuntu CD, and I was not sure how to access the MBR partition table.  Do I delete the entire MBR partition table?  Is there a "diskutil list" equivalent in Linux?

By they way, thanks ALOT for all of you help.

---

### Post by cyberdork33 on 2008-08-19
> **rrm74001 said:**
> What partition exactly am I sipposed to delete? If I go to Disk Utility, it only shows one partition, and it is for the "Macintosh HD".you are not deleting any partition really, just the MBR table.

> **rrm74001 said:**
> If I go to the Startup Disk Preference Pane, it also only shows one partition, and it is for the "Macintosh HD". See Screenshot:
don't use this utility to dual boot with Ubuntu. It will will only cause problems. rely on refit and the boot chooser menu only.

> **rrm74001 said:**
> Finally, if I type into the Terminal "diskutil list", it returns this:
The above image looks normal to me.All the above is normal for you situation.

> **rrm74001 said:**
> The EFI boot menu seems to be the only thing that can see this "Windows" drive. There is no "windows drive" It just sees that there is bootable code in the MBR as you can see in the output here:

```
MBR contents:
 Boot Code: Unknown, but bootable
```

> **rrm74001 said:**
> I booted into my Live Kubuntu CD, and I was not sure how to access the MBR partition table. Do I delete the entire MBR partition table? Is there a "diskutil list" equivalent in Linux?

> **cyberdork33 said:**
> If you want to remove the Windows icon, I think that your best bet is to boot the ubuntu livecd and use the _*fdisk*_ tool to remove the partitions (fdisk can only access the MBR table, not your GPT).
Yea fdisk. fdisk is not capable of reading (or modifying) a GPT. (PS, I am unsure of the ability of fdisk in OSX, use the version on the ubuntu live cd)

You might also be able to completely clear the MBR like so:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

---

### Post by rrm74001 on 2008-08-19
> **cyberdork33 said:**
> you are not deleting any partition really, just the MBR table.


don't use this utility to dual boot with Ubuntu. It will will only cause problems. rely on refit and the boot chooser menu only.

All the above is normal for you situation.

 There is no "windows drive" It just sees that there is bootable code in the MBR as you can see in the output here:

```
MBR contents:
 Boot Code: Unknown, but bootable
```




Yea fdisk. fdisk is not capable of reading (or modifying) a GPT. (PS, I am unsure of the ability of fdisk in OSX, use the version on the ubuntu live cd)

You might also be able to completely clear the MBR like so:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

The MBR Partition Table is not supposed to be there at all right?  So completely getting rid of it will not affect anything?  The only thing I should have on my hard drive is a GUID Partition Table, and a EFI and Macintosh hard drive partitions?

---

### Post by cyberdork33 on 2008-08-19
> **rrm74001 said:**
> The MBR Partition Table is not supposed to be there at all right?  So completely getting rid of it will not affect anything?  The only thing I should have on my hard drive is a GUID Partition Table, and a EFI and Macintosh hard drive partitions?
yes / no. Can it not be there and be OK? yes. OSX boots from EFI, and EFI uses the GPT. MBR is only used for so-called "legacy" operating systems.

---

### Post by rrm74001 on 2008-08-19
> **cyberdork33 said:**
> yes / no. Can it not be there and be OK? yes. OSX boots from EFI, and EFI uses the GPT. MBR is only used for so-called "legacy" operating systems.

Okay I see.  My goal for right now is just to restore it back to the way it was.  So when Apple ships their computers, do they include an empty MBR Partition Table?  I plan on installing Windows in the near future, so should I just clear out the MBR using:

```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

Or should I also delete the partition table (keeping in mind that I just want to restore my hard drive back to factory settings)

?

---

### Post by cyberdork33 on 2008-08-19
> **rrm74001 said:**
> Okay I see.  My goal for right now is just to restore it back to the way it was.  So when Apple ships their computers, do they include an empty MBR Partition Table?  I plan on installing Windows in the near future, so should I just clear out the MBR using:

```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```Or should I also delete the partition table (keeping in mind that I just want to restore my hard drive back to factory settings)

?
if you are going to install windows (using boot camp I presume) then that will fix it and you don't have to take any risk. just open the bootcamp assitant and see if it will allow you to partition the hard drive.

---

### Post by rrm74001 on 2008-08-19
> **cyberdork33 said:**
> if you are going to install windows (using boot camp I presume) then that will fix it and you don't have to take any risk. just open the bootcamp assitant and see if it will allow you to partition the hard drive.

Okay so I ran the following commnad to backup the MBR:

```
sudo dd if=/dev/sda of=/home/username/mbr_backup bs=512 count=1
```

I ran the following command to overwrite the MBR:

```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

And the "Windows" drive disappeared!  Partition Inspector now reports this:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    488134983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    488134983  af  Mac OS X HFS+

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active
```

It does not look like the MBR has been touched at all.  Is it normal for the MBR contents to say "None" now?

Thanks for all of your help!  I am going to take a break from Linux for a few days.  I have become frustrated with Linux for about two weeks now.  (Of course, I have been trying to avoid installing to the internal drive at all costs, which I now know is my only option.)  I will try again by installing to the internal drive in a few days.

Would I be able to install to an external hard drive if I used a virtual machine?

---

### Post by cyberdork33 on 2008-08-19
> **rrm74001 said:**
> Okay so I ran the following command to backup the MBR:

```
sudo dd if=/dev/sda of=/home/username/mbr_backup bs=512 count=1
```I ran the following command to overwrite the MBR:

```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```And the "Windows" drive disappeared!  Partition Inspector now reports this:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    488134983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    488134983  af  Mac OS X HFS+

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active
```It does not look like the MBR has been touched at all.  Is it normal for the MBR contents to say "None" now? You chose to empty the MBR bootcode (which caused the windows icon), but left the MBR partition table. So, your output seems logical. Did you have Windows installed previously or something? I would guess that what was in the MBR was leftover Windows bootloader.

> **rrm74001 said:**
> Thanks for all of your help!  I am going to take a break from Linux for a few days.  I have become frustrated with Linux for about two weeks now.  (Of course, I have been trying to avoid installing to the internal drive at all costs, which I now know is my only option.)  I will try again by installing to the internal drive in a few days.

Would I be able to install to an external hard drive if I used a virtual machine?You can certainly use a VM. However, installing to a VM is very different from installing on you Mac directly. For one thing, you do not install on a real disk, you install on a "virtual" disk (literally it is a drive image file that you create). You can put this virtual drive file on your external or internal, it doesn't matter (it is just a file afterall, that you can delete). Having the drive image on your external drive though, will likely cause the VM to run a bit slower. I would recommend leaving it on the main drive unless you do not have the space.

VirtualBox is free and has many of the features of the pay-for VMs out there. My second choice after that would be Vmware Fusion. Good luck! If you ever need help installing in the future feel free to drop by and ask your questions.

---

