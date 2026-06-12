---
title: "Find Hard Drive model"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Gimpy_Rob on 2007-08-22
I'm buying a new drive for a server running ubuntu server, but I don't have physical access to it at this exact point in time.  Is there a way to get the kind of information bios displays about the drive? IE, the model of the drive?


Fdisk -l doesn't provide enough.

Thanks for any help.

---

### Post by DeHorde on 2007-08-22
sudo hdparm -i /dev/sda 
or 
sudo hdparm -i /dev/hda
depending on whether its a scsi (or detected as a scsi) or an ide  drive

---

### Post by Inxsible on 2007-08-22
> **Gimpy_Rob said:**
> I'm buying a new drive for a server running ubuntu server, but I don't have physical access to it at this exact point in time.  Is there a way to get the kind of information bios displays about the drive? IE, the model of the drive?


Fdisk -l doesn't provide enough.

Thanks for any help.Never mind :rolleyes:  ....post deleted

---

### Post by Gimpy_Rob on 2007-08-22
:)  Perfect!

Thanks!

---

