---
title: "hard drive help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by draze on 2008-01-27
hello.

my question is not really a linux question but it is for linux.

i wanted to buy a bigger hard drive to install ubuntu on it + extra space for movies and music. so i bought one. now i have a problem with my new hard drive. it's a WesternDigital 500gb 7200 16mb Sata-2 hard drive. i installed it right i'm sure about it. 
now the problem is that my bios sees both of my hard drives the Maxtor 80gb IDE with XP on  as a master  it and the WD 500gb one. but my windows does not see my 500gb hard drive. 

plz help.

i tried booting through ubuntu live, it does recognize the drive but says it has no file system...so i tried to partition it with gparted...it kept crashing for some reason, but i think i did it. but windows still won't detect...plz help.

---

### Post by dcstar on 2008-01-27
> **draze said:**
> 
...........
i tried booting through ubuntu live, it does recognize the drive but says it has no file system...so i tried to partition it with gparted...it kept crashing for some reason, but i think i did it. but windows still won't detect...plz help.

The gparted on the current live CD has a bug which crashes it when it tries to refresh, there is a fixed version you can install via Synaptic whilst in a live session that won't crash.

As for your Windows problem, possibly until you format the drive with a filesystem that Windows can understand then it will be visible in the Disk Manager.

---

### Post by swoll1980 on 2008-01-27
A driver needs to be installed maybe?

---

### Post by draze on 2008-01-27
> **dcstar said:**
> The gparted on the current live CD has a bug which crashes it when it tries to refresh, there is a fixed version you can install via Synaptic whilst in a live session that won't crash.

As for your Windows problem, possibly until you format the drive with a filesystem that Windows can understand then it will be visible in the Disk Manager.

 what do you mean synapic whilst?

---

### Post by draze on 2008-01-27
actually i just solved my problem myself. i just reinstalled my Raid drivers.

---

