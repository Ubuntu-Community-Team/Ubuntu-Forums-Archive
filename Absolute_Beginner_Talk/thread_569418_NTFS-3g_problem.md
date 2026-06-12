---
title: "NTFS-3g problem"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Acoustyk on 2007-10-07
Hey all, quick question, I just installed ntfs-3g configuration tool from the repository and rebooted.  I still cannot write to the NTFS drive.  Any ideas? (Yea im a noob)

P.S.  Anybody know off-hand what the command is to get the stable version of compiz-fusion?  or at least where I can get a .deb version?

---

### Post by taurus on 2007-10-07
Can you mount your Windows partition with ntfs-3g?  Is there any error message?  Maybe you need to boot into Windows first and shut it down properly before you can mount and write to it from Ubuntu.

---

### Post by wolfen69 on 2007-10-07
did you go to system tools>ntfs config  first? you need to do that before you  have read/write.

---

### Post by Acoustyk on 2007-10-07
> **taurus said:**
> Can you mount your Windows partition with ntfs-3g?  Is there any error message?  Maybe you need to boot into Windows first and shut it down properly before you can mount and write to it from Ubuntu.

No there is no error message and I did reboot in windows and the drive is mounted.  I went to system tools checked the boxes and rebooted but still no dice.  What happens is when I try to save it says that the medium is read-only and asks if I want to save a copy on another drive.

---

### Post by Hospadar on 2007-10-07
Were you sure to actually run the config tool and make the drives writable?

---

### Post by Acoustyk on 2007-10-07
Not sure what you mean.  I just installed it.

---

### Post by logos34 on 2007-10-07
in a terminal run
[B]
sudo ntfs-config[/B]

 x enable write support

---

### Post by spaceghoti on 2007-10-07
> **logos34 said:**
> in a terminal run
[B]
sudo ntfs-config[/B]

 x enable write support

I've done this, but I still get nothing when I attempt to boot my NTFS-formatted USB hard drive.  I can mount it from a Windows box, but not Kubuntu.

When I run **lsusb** it shows up as *Bus 003 Device 004: ID 048d:8903 Integrated Technology Express, Inc.*

---

### Post by logos34 on 2007-10-07
> **spaceghoti said:**
> I've done this, but I still get nothing when I attempt to boot my NTFS-formatted USB hard drive.  I can mount it from a Windows box, but not Kubuntu.

When I run **lsusb** it shows up as *Bus 003 Device 004: ID 048d:8903 Integrated Technology Express, Inc.*

Post your /etc/fstab file and fdisk

sudo fdisk -l

---

