---
title: "Vmware cannot access USB drive"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-06-28
I have having a problem with XP under Vmware, I have a sandisk U3 drive that I can access under Feisty, however, it does not mount in XP though Vmware.  I have tried it with it mounted in Ubuntu and unmounted in Ubuntu and although the drives show in My Computer I get an error message stating that the shortcut is not available.

I have gone though the automated add hardware process in XP but to no avail.

The U3 drive works on my XP machine at work but not though Vmware, my main reason for wanting to connect it is so that I can remove the damned U3 software, I don't have admin rights at work so I am currently stuck with it.

---

### Post by scxtt on 2007-06-28
just so we're clear, have you added a USB device to your VM?  and when the VM's on, did you connect the device to the VM?

---

### Post by ushills on 2007-06-28
Yes, I added the USB to the Vmware device configuration, XP then pick up the device and installs the USB drivers.  With U3 this results in both a CD-Rom and Flash drive being added to My Computer, but when I click on either it say the shortcut is invalid.

I have tried it with the USB mouted in both Ubuntu and XP and just under XP - no difference.

Incidently a UDF DVD-ram that I have mouted in both Ubuntu and XP can be read by both the VM and Ubuntu.

---

### Post by Big_Croc7 on 2007-06-28
Have you tried formatting it?

---

### Post by ushills on 2007-06-28
> **Big_Croc7 said:**
> Have you tried formatting it?

Can't access it in XP to format it, in ubuntu formating only formats the accessible part of the drive.

---

### Post by Big_Croc7 on 2007-06-29
Hmm... here's an idea - I don't know if it will work though, and it is quite risky.  Look into it in more detail and backup all data first ;-)

You could try using the 'dd' command.  This writes directly to the specified file or device.  So, for example, you could use something like:
```
dd if=/dev/zero of=/dev/sdbX bs=16384 count=YYY
```
where sdbX is the device path for your USB disk (it dosen't have to be mounted) and bs times YYY is the total size of the disk (in bytes)..

This will write zeros to the target specified at 'of' for as long as bs times count.  Hopefully, this will happily write to the entire USB disk, ignoring anything on it (partitions etc will be ignored).  Be careful though - if you write, for example, 'sda' as the output, this will overwrite your first harddisk, starting with the boot record and wiping out your system.  You have been warned!
:-)

---

