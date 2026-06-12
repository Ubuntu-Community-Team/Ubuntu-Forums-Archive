---
title: "New install does not boot up"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by tmcdlive on 2007-12-26
DID  INSTALL ON NEW PC WITH DIFFERENT DISTRO ON IT ... NO WINDOWS ON PC.

Results are that the machine does NOT boot in to Ubuntu from hard-drive. It boots into the native distro but not Ubuntu ....  from hard drive.

It does boot in Ubuntu via the Live-CD.

It does boot into the Original Operating system on this PC -- gOS Linux Distro -- remember this is a Linux machine (made by Everex) and does not have windows on it. I am "replacing" the gOS on it.

Does not Boot into Ubuntu from the Hard Drive.

Install went smoothly and pretty quick .. the one quirk was that there was no ending message saying finished ... the sliding bar "installation" screen finished and cleared off the desktop ... and we were back to the Live-CD system.

I waited about 15 minutes and absolutely nothing was going on. No activity on Hard-drive nor on the CD. So using the instructions on the "Howtoforge" instruction page I booted it with the results mentioned above.

Question ... Any ideas on what to do?

Thanks much for any help.  By the way, I am new to Linux so use the KIS principle.  :confused:

---

### Post by %hMa@?b&lt;C on 2007-12-26
when you boot up to the GRUB menu, try doing the "failsafe" or "recovery" option.  Post any errors that you encounter.

---

### Post by Sef on 2007-12-26
From the Live CD, let's check your partitions:

Applications > Accessories > Terminal

then type

```
sudo fdisk -l
```

Paste the results here.

---

