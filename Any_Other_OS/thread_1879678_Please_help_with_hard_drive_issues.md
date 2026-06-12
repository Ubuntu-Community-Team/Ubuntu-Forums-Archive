---
title: "Please help with hard drive issues"
date: 2011-11-12
forum: Any Other OS
---

### Post by PoseidonOSU on 2011-11-12
I am helping a friends who has a Windows 7 laptop. I have figured out it is some problem with the hard drive. I have tried to diagnose it with several programs and all it does is hang. When I put it in a USB enclosure and tried ot attach it to my laptop this is the huge error it vomited up.the drive is a Western Digital 500GB Serial ATA. He just wants some data off the disk. 


Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=84202 count=1 br=-1: Input/output error
Failed to mount '/dev/sdb3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by BillyBoa on 2011-11-12
You have a problem with the hard drive, is failing.

Try to run the CHKDSK /f option and the as the system explains reboot twice.

---

### Post by Paqman on 2011-11-12
Most likely what has happened is that the drive has not been shut down cleanly. If you still have Windows available, plug the drive in and boot up into Windows, open up the drive, then use the "safely remove" option and shut down Windows. It should then mount cleanly in Ubuntu.

There's also a way to force it to mount in Ubuntu without using Windows, let us know if you need to do that.

---

### Post by rng on 2011-11-12
If mounting fails by all means (which is unlikely), you can use ddrescue/dd_rescue/myrescue to read directly from hard disk. The applications are available in synaptic package manager.

---

### Post by Perfect Storm on 2011-11-12
Moved to Other OS/Distro Talk.

---

### Post by Mark Phelps on 2011-11-12
> **rng said:**
> If mounting fails by all means (which is unlikely), you can use ddrescue/dd_rescue/myrescue to read directly from hard disk. The applications are available in synaptic package manager.

Except, it's an NTFS file system -- and even if they do recovery all the data, it still will NOT mount -- because it was an unclean mount. And, if the partition table was in an unclean state, the filesystem will be unreliable until it is fixed.

The best recourse was already mentioned -- run CHKDSK on an MS Windows PC.

---

### Post by coffeecat on 2011-11-12
> **BillyBoa said:**
> You have a problem with the hard drive, is failing.

Not necessarily a hardware fault, although a possibility 

> NTFS is either inconsistent, **or** there is a hardware fault, **or** it's a
SoftRAID/FakeRAID hardware.

@PoseidonOSU, +1 to the suggestions to run chkdsk. The most likely of those three is an inconsistent NTFS filesystem and this should be repairable.

One thing you could try. Is this 500GB disc the system disc from the laptop containing the Windows 7 OS? If so, put it back in the laptop and press F8 when you first switch on. This gives you the advanced startup menu and one option is "repair your computer". **If** the recovery tools are installed in the Windows system you should be able to repair the NTFS filesystem from this. An alternative is if you can get hold of a Windows 7 repair CD (you can create this from any working Windows 7 system). Boot up with the repair CD and run chkdsk from the the command prompt.

---

