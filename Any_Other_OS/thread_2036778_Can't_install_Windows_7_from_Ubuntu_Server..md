---
title: "Can't install Windows 7 from Ubuntu Server."
date: 2012-08-02
forum: Any Other OS
---

### Post by jazzy348 on 2012-08-02
Hi,

I have Windows 7 on a disk but when inserting the disk to my computer and waiting for the "press any key to boot from disk" it doe not show. Then it boots Ubuntu Server as normal. Is there any way of loading the setup disk from Ubuntu Server?

Thanks,
Jazzy.

---

### Post by Beacon11 on 2012-08-02
The BIOS is one's computer is configured to look for bootable filesystems on multiple media devices in a specific order, and boot from the first one it sees. Your problem is that this "specific order" has your hard drive before your disk drive, so it always boots from Ubuntu first. You need to enter your BIOS settings (look at the boot splash screen-- you should see something like "Press F2/delete/F10/somekey to enter setup." Look for the Boot menu, and change boot priorities so your disk drive is higher than your hard drive.

---

