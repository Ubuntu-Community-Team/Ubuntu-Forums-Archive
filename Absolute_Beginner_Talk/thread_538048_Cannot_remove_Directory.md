---
title: "Cannot remove Directory"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by forevereating on 2007-08-29
When I try to eject my usb flash drive or external HDD (both in FAT32), I get an error saying "cannot remove directory". Although it does disappear from the desktop after ejecting. I didn't have this problem like a week ago, I've been using feisty and this usb drive for months. Please tell me whats wrong? ty.

---

### Post by PetePete on 2007-08-29
can you post anything from /var/log/syslog from around the time you try to eject? might give some clues

---

### Post by aysiu on 2007-08-29
It probably mounted read-only for whatever reason. Maybe this'll help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by forevereating on 2007-08-29
No it wasn't mounted as read-only. And I don't think removable drives such as this usb HDD needs to be in the fstab.

Here's the log (this would be after ejecting, gives no log, then manually switching HDD off it gives the first line in the log. Then I switched it back on.):

```
Aug 29 18:24:26 Linux kernel: [ 9518.552990] usb 5-8: USB disconnect, address 6
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.090702] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.098201] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_C01B_0671'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.099214] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host_scsi_device_lun0'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.099985] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.100774] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_usbraw'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.102142] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.103357] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355'). 
Aug 29 18:24:26 Linux NetworkManager: <debug info>^I[1188437066.107755] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WDC_WD25_00BB_22DWA0_DEF106207355_0_0'). 
Aug 29 18:24:34 Linux kernel: [ 9526.729388] usb 5-8: new high speed USB device using ehci_hcd and address 7
Aug 29 18:24:34 Linux kernel: [ 9526.864832] usb 5-8: configuration #1 chosen from 1 choice
Aug 29 18:24:34 Linux kernel: [ 9526.865087] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 29 18:24:34 Linux kernel: [ 9526.865165] usb-storage: device found at 7
Aug 29 18:24:34 Linux kernel: [ 9526.865168] usb-storage: waiting for device to settle before scanning
Aug 29 18:24:34 Linux NetworkManager: <debug info>^I[1188437074.446758] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355'). 
Aug 29 18:24:34 Linux NetworkManager: <debug info>^I[1188437074.518960] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0'). 
Aug 29 18:24:34 Linux NetworkManager: <debug info>^I[1188437074.525765] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host'). 
Aug 29 18:24:34 Linux NetworkManager: <debug info>^I[1188437074.547943] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_usbraw'). 
Aug 29 18:24:39 Linux kernel: [ 9531.863582] usb-storage: device scan complete
Aug 29 18:24:39 Linux kernel: [ 9531.867578] scsi 6:0:0:0: Direct-Access     WDC WD25 00BB-22DWA0      0000 PQ: 0 ANSI: 0
Aug 29 18:24:39 Linux kernel: [ 9531.868933] SCSI device sdf: 488397168 512-byte hdwr sectors (250059 MB)
Aug 29 18:24:39 Linux kernel: [ 9531.869804] sdf: Write Protect is off
Aug 29 18:24:39 Linux kernel: [ 9531.869809] sdf: Mode Sense: 27 00 00 00
Aug 29 18:24:39 Linux kernel: [ 9531.869838] sdf: assuming drive cache: write through
Aug 29 18:24:39 Linux kernel: [ 9531.870803] SCSI device sdf: 488397168 512-byte hdwr sectors (250059 MB)
Aug 29 18:24:39 Linux kernel: [ 9531.871678] sdf: Write Protect is off
Aug 29 18:24:39 Linux kernel: [ 9531.871683] sdf: Mode Sense: 27 00 00 00
Aug 29 18:24:39 Linux kernel: [ 9531.871687] sdf: assuming drive cache: write through
Aug 29 18:24:39 Linux kernel: [ 9531.871691]  sdf: sdf1
Aug 29 18:24:39 Linux kernel: [ 9531.893238] sd 6:0:0:0: Attached scsi disk sdf
Aug 29 18:24:39 Linux kernel: [ 9531.893306] sd 6:0:0:0: Attached scsi generic sg7 type 0
Aug 29 18:24:39 Linux NetworkManager: <debug info>^I[1188437079.477398] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host_scsi_device_lun0'). 
Aug 29 18:24:39 Linux NetworkManager: <debug info>^I[1188437079.491973] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF106207355_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 29 18:24:39 Linux NetworkManager: <debug info>^I[1188437079.654590] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WDC_WD25_00BB_22DWA0_DEF106207355_0_0'). 
Aug 29 18:24:39 Linux NetworkManager: <debug info>^I[1188437079.687760] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_C01B_0671'). 
Aug 29 18:24:39 Linux hald: mounted /dev/sdf1 on behalf of uid 1000
```

So any ideas? Its just really frustrating that everything is going along fine then one day all of a sudden you get an error for no apparent reason. Oh, btw the error actually said:

**      Cannot unmount volume**
      Cannot unmount the volume 'USB_HDD'.
Details
      Cannot remove directory

---

### Post by forevereating on 2007-08-29
Okay, for some reason it just fixed it self. I guess things just happen??? But I do have to note that I did edit my fstab BUT the ONLY thing I changed was my windows partition, I changed the format from NTFS to NTFS-3g, thus allowing read/write into windows' ntfs filesystem. This should not have fixed my unmounting error. So I *am* still looking for an answer in the hopes that if it does happen again I would know what to do. Thanks for reading...

---

### Post by Harpoon on 2007-08-29
I have also had this appear "out of the blue."  The only two things I can attribute it to are:  a recent update having unintended consequences (?), or my having installed ntfs-config and having it mount all fixed and removable ntfs partitions as rw.

However, I have two identical (except for file contents) ext3 usb disks.  One unmounts without incident, the other returns this "error."  I put "error" in quotes because the drive does, in fact, unmount (using the simple right click on the icon) method. Successful unmount confirmed with "fdisk -l".

At the moment, this is only an annoyance.  Let's hope it doesn't sprout wings and morph into a full blown problem.

---

### Post by Harpoon on 2007-08-29
Sorry, I hit post too fast.

I also checked the syslog, and the only entry at the time I unmounted the two drives was the one showing that the drive was successfully unmounted on behalf of user 1000.

No mention of the troublesome drive.

---

### Post by vanadium on 2007-08-30
I recently see this problem myself, currently with an USB stick. I guess that it is just an annoyance without severe consequences, because the drive is effectively unmounted (does not anymore appear in the listing of "mount", although it is not "ejected" (still shows up in sudo fdisk -l). Then there is this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/91854](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/91854). It is better than the bug earlier in Edgy, where the volume wasn't unmounted at all ([https://bugs.launchpad.net/ubuntu/+bug/99538](https://bugs.launchpad.net/ubuntu/+bug/99538))

---

### Post by forevereating on 2007-09-01
The problem has came back. I agree with Harpoon, it has to do with an update. And when I eject it, it does *not* unmount. This problem is very troublesome. I hope it gets fixed soon. Also it seems like I am not the only person experiencing this, it also seems to be a recent problem. Is there any way I can help get this problem fixed sooner?

---

### Post by sup3roque on 2007-09-01
one more with that problem... :S

---

### Post by nonewmsgs on 2007-09-01
i had that same issue.  everything else could be added or removed but this one directory.  windows wouldnt do it either but would change it's name and after i refreshed it, a file with the new name would be there and the directory i tried to rename.  then the next ubuntu mount it let me.  idk why?

---

### Post by forevereating on 2007-09-04
bump

---

### Post by meastp on 2007-09-15
> **sup3roque said:**
> one more with that problem... :S

+1 :(

---

### Post by FuturePilot on 2007-09-16
Wow, this is happening to me too. It just appeared out of the blue. It was fine just a couple of days ago.:confused:

---

### Post by FuturePilot on 2007-09-16
I seem to have found a fix. Remove /media/.hal-mtab
It seems to be a bug with stale entries in the file. It's a hidden file so if you use a root nautilus to remove it, make sure to show hidden files.

---

### Post by vanadium on 2007-09-24
Indeed, deleting the file solves the issue. I guess it is only temporary, though. I suspect it might return when you plug in another drive with a different file system, then plug back in your USB stick.

Having the issue, the contents of /media/.hall-mtab looked like:

/dev/sdb1	1000	0	ntfs-3g	noexec,nosuid,nodev,locale=en_US.UTF-8,exec	/media/Silverscreen

which clearly relates to my ntfs formatted Lacie Silverscreen and not to my USB. Yet I already loaded a different USB stick this morning. I deleted the file, and it was recreated upon remounting the USB-stick to read:

/dev/sdb1	1000	0	vfat	noexec,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec	/media/USB

On unmounting the drive, the file is "emptied". I'll do some more testing when I have my silverscreen available. For the moment, mounting and unmounting the USB works fine.

---

