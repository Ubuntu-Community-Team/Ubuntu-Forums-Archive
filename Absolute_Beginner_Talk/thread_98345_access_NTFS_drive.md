---
title: "access NTFS drive"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by dronepower on 2005-12-03
I just mounted my 2 SATA NTSF drives, but they can only be accessed by the root user. Can I only log in as root in terminal mode?

How can I change it so all users can acess those drives?

---

### Post by jorn on 2005-12-03
Hi!
Try this: [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
Jorn

---

### Post by dronepower on 2005-12-03
ahh tnx, so all i need is to look up for the code so users can read and write.

---

### Post by jorn on 2005-12-03
To have root access in nautilus type in rerminal:
gksudo nautilus

Jorn

---

### Post by Ted_Smith on 2005-12-03
That starters guide is amazing! I'd spent ages trying to figure out how to gain access to my NTFS drives. And every step of that guide worked first time!

Well written

Ted

---

### Post by aysiu on 2005-12-03
[QUOTE=dronepower]ahh tnx, so all i need is to look up for the code so users can read and write.[/QUOTE] Users will not be able to *write* to NTFS from Linux. That's experimental, unstable, and/or dangerous as of now. NTFS should be read-only. If you want read/write, consider making a FAT32 partition to share between OSes.

---

### Post by atoponce on 2005-12-03
[quote=aysiu]Users will not be able to *write* to NTFS from Linux. That's experimental, unstable, and/or dangerous as of now. NTFS should be read-only. If you want read/write, consider making a FAT32 partition to share between OSes.[/quote]

A seperate partition is definitely the best option, however, there are many others for sharing data between NTFS and Linux partitions for both read/write.  Unfortunately, they all require rebooting.  Oh well.  Listed from most expensive to least:

* Use an external hard drive, and format at FAT32
* Use a USB thumb drive
* Burn blank CDRWs or DVD-RWs
* Access a FTP/SSH site

As aysiu mentioned, writing to an NTFS drive isn't supported, and could cause data corruption and/or drive failure.  However, it is in the kernel, so downloading the sources, enabling it, and recompiling would allow you to write to an NTFS drive.  You would probably be better off with one of the other options mentioned.

---

