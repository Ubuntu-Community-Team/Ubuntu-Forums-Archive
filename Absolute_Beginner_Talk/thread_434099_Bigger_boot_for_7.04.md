---
title: "Bigger /boot for 7.04?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by NAT2007 on 2007-05-05
I'm trying to upgrade from 6.10 to 7.04 over the Internet and it aborts with a complaint about not enough space on my /boot partition.
The /boot partition is ~30MB, of which currently 10MB are used and ~17MB are available. The upgrade process asks for at least 23.7MB free space on /boot, so I'm ~7MB short.
Since there's nothing on my /boot I can get rid of (there's just one kernel there, and grub) I will have to resize my partitions (somehow, using GParted; hopefully it's possible, since the partition after /boot is / ), but before I do that I was wondering why 7.04 requires so much space on /boot.

If 6.10 can get by using 10MB, why does 7.04 need >20MB?

---

### Post by Bachstelze on 2007-05-05
Why did you make a /boot partition anyway ? There's not much use to it if you're just running one Linux.

---

### Post by NAT2007 on 2007-05-05
Because I'm stupid? Who knows why I did what I did years ago when I did it? The question is what do I do now?
Actually, the question is what's with Feisty and its super-boot?:)

---

### Post by sad_iq on 2007-05-05
> **HymnToLife said:**
> Why did you make a /boot partition anyway ? There's not much use to it if you're just running one Linux.
 Well actually it's the only thing that allowed me to install 7.04 on my pc...some stupid raid stuff and grub errors!!! But maybe I need to learn more about installing Ubuntu!!! :lolflag:

---

### Post by NAT2007 on 2007-05-05
Ok, I found the answer to my problem [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=414639&page=2&highlight=%2Fboot+size+feisty"), it seems to have to do with the way the upgrade process calculates its space requirements on /boot (actually, the way it DOESN'T calculate but instead just assumes you need 40MB). There are some workarounds, but no fix yet.

---

