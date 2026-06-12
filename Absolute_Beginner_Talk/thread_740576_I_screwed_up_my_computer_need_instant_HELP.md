---
title: "I screwed up my computer need instant HELP"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Iscreweupmycomp on 2008-03-30
my computer cant detect the C drive and Xp wont boot i am so screwed
HELP!

---

### Post by Tatty on 2008-03-30
Hi, what happened before your computer stopped booting?

Try booting to a Ubuntu live CD and see if you can mount your hard disk in there.

---

### Post by Hospadar on 2008-03-30
you should boot off the livecd and do an Alt-F2 and type "sudo gparted" and see if there is a big ntfs partition on any of your drives.  if there isn't, you may have accidentally deleted your windows partition.

Please also post the output of "df"

Open a terminal (Applications->Accessories->Terminal) and type "df" (no quotations) this command gives info about all your drives and partitons.

It's possible that your windows boot partitions just got messed up, which is easy to correct, but it's also possible you wiped your windows install.

"Shields down, brace for impact"

---

