---
title: "Not able to mount windows partition in ubuntu!"
date: 2012-05-13
forum: Any Other OS
---

### Post by paivas on 2012-05-13
Hi,

Recently, my laptop failed to boot up with Windows 7. I tried repair using recovery disk, but of no use. It is not able to get in to the Recovery wizard itself.

Then I created Ubuntu bootable flash drive and tried to repair in Ubuntu.
But surprisingly it has failed to mount my Windows OS drive, with the following error message.

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more detail

I tried, ntfsfix dev/sda3(which is my OS drive), which says drive can be mounted and processed successfully.

please help me in this regard!

**_Main motive of mine is to recover all the data present in windows OS drive._**

---

### Post by oldfred on 2012-05-13
Welcome to the forums.

Moved to Other OS

Ubuntu normally will not mount a NTFS partition that needs chkdsk to prevent further damage that then chkdsk would not be able to repair. ntfsfix just does a few minor thing and sets the chkdsk flag, so when you Boot Windows it will run chkdsk.

You need to run your Windows repairCD or USB and run chkdsk.

If you did not do this before, find a friend with the same (32bit or 64bit) version of Windows.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to recommend a site for a free download of a repair only ISO, but Microsoft makes them charge $10 now.
See Mark Phelps post below for another site that has a repair ISO.

---

### Post by Mark Phelps on 2012-05-13
The Linux utility NTFSfix can only repair the most trivial of NTFS related problems.  Any major such problems have to be repaired using MS Windows.

Since you apparently can't access your Windows filesystem from a LiveUSB, you will need to consider a couple of other options:
1) Repairing the Windows filesystem using Windows utilities -- the BEST approach.  Go to the Partition Wizard website and download their ISO image and burn that to PC (using an MS Windows PC).  Boot from that and use their options to Check the drive -- that will run CHKDSK on the drive -- and should make it mountable again.
2) Remove the hard drive from your PC, connect it to an MS Windows PC, and run CHKDSK from there.

Sorry, but only CHKDSK is really able to repair major NTFS problems and that can only be run using MS Windows.

---

