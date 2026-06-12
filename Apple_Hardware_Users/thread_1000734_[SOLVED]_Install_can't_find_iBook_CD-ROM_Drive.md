---
title: "[SOLVED] Install can't find iBook CD-ROM Drive"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by pwaldo on 2008-12-03
Hi all,

I have an old iBook that is currently running Kubuntu fiesty.  I want to wipe the root and start an Ubuntu Intrepid install from scratch.  I boot from the install CD, but it quickly complains it can't find a CD Drive.  It does not seem to be a hardware problem, as the CD Drive works fine under Fiesty and OSX

dmesg says that the kernel detected hda and hdb (the CD Drive) on ide0. "ls /dev/hd*" shows me that only /dev/hda exists; no /dev/hdb.  I have tried insmodding any driver that might be related to ATA or IDE.

Any ideas?  Thanks in advance!

---

### Post by mkvnmtr on 2008-12-03
I believe there is another thread here, should be on the first two pages, that deals with this problem. I am using an Ibook also butn haven't done the upgrade yet.

---

### Post by pwaldo on 2008-12-03
> **mkvnmtr said:**
> I believe there is another thread here, should be on the first two pages, that deals with this problem.

Apparently the solution is to ```
modprobe ide-scsi
```I'll give it a try tonight.  Thanks!

---

### Post by pwaldo on 2008-12-04
> **pwaldo said:**
> Apparently the solution is to ```
modprobe ide-scsi
```I'll give it a try tonight.  Thanks!
That did the trick!

---

