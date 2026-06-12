---
title: "No CD Boot in BIOS"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by coz21 on 2007-01-16
Hello,

I am running an older laptop where the BIOS doesn't consider the CD-ROM a boot device. How do I work around this so I can install Ubuntu on my machine?

Thx!

---

### Post by kidders on 2007-01-16
Hi there,

Depending on your level of expertise, you could probably install Ubuntu without booting from the install disc ... but it would be a lot more trouble than it's worth imo. If your laptop is *that* old, I doubt Ubuntu is the right OS for it. What are the specs?

---

### Post by logos34 on 2007-01-16
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
[https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)

---

### Post by noo2bunto on 2007-01-16
I had some luck with SmartBoot.  I used it to create a 3.5" floppy disk that upon loading provides you with a list of devices from which you'd like to boot.  E.g., CD-ROM, Hard Drive, etc.

---

### Post by phr0ze on 2007-01-16
Look for a SCSI or Other as boot devices in the BIOS too. Although it's not a SCSI device, the BIOS might lump it in there.

---

