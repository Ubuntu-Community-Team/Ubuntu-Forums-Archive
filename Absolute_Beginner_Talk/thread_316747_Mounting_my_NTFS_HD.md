---
title: "Mounting my NTFS HD"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by myslin on 2006-12-11
I'm a total Linux begginer and I'm currently dual booting Windows/Linux and I want to read mp3 files from my NTFS HD and I'm having trouble mounting it. I'm not sure which I should mount, HDA SDA SDA1? I tried doing fdisk -l but it does not return any results.
I've already created /media/windows and tried sudo mount (/dev/hda // /dev/sda // /dev/sda1) /media/windows -t ntfs -o nls=utf8,umask=0222 with no luck. Gparted lists my ntfs drive as /dev/sda.
My 2 drives are 
120GB SATA Seagate Barracuda - Full NTFS
80GB SATA Maxtor - Linux Drive
Any help you can give me would be greatly appreciated.

---

### Post by xyz on 2006-12-11
This should help:
[ Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")
Hope it helps. Let us know...

---

### Post by taurus on 2006-12-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by myslin on 2006-12-11
IT WORKED! Thank you very much for the quick replies, next time I'll try to dig around the forums more :)

---

### Post by xyz on 2006-12-11
> **myslin said:**
> IT WORKED! Thank you very much for the quick replies, next time I'll try to dig around the forums more :)
Feels good, doesn't it?
Good luck and welcome here.

---

