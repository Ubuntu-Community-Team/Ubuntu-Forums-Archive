---
title: "firefox doesn't start; ubuntu doesn't shutdown..."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-12-30
does anyone know why firefox refuses to start ? i mean, after i click on it, it appears on taskbar with the title "Starting Mozilla" but disappears after 5-6 seconds. i even reinstalled it from synaptic package manager and still the same problem...

i currently have like 100% of ubuntu partition (ext2) full (i only have like 100mb left) and i thought it might be because it doesn't have enough space for caching or i dont know. thats why i reinstalled it...

after reinstalling mozilla, i've installed gparted but i don't know where to find it!

another thing would be that ubuntu doesn't shutdown! when i press that red icon the pannel comprising restart, shutdown, logout etc doesn't appear :(! and the taskbar and other bar dissapear...

pls help:confused:!

thanx...

---

### Post by nick_h on 2007-12-30
> does anyone know why firefox refuses to start ?
Start it from the command line and see what error messages you get.

> i currently have like 100% of ubuntu partition (ext2) full
Bad news.  This may well be the cause of your problems.

> i've installed gparted but i don't know where to find it!
System->Administration->Partition Editor

> another thing would be that ubuntu doesn't shutdown!
Try:
```
sudo shutdown -h now
```

---

### Post by the_nomad on 2007-12-30
in commandline when trying to open firefox says:
> Segmentation fault (core dumped)

gparted starts well but remains at "Scanning devices..." ... and it stays... and i don't think it's too normal :(

shutdown worked too.

---

### Post by nick_h on 2007-12-30
> gparted starts well but remains at "Scanning devices..." ... and it stays... and i don't think it's too normal 
It only scans for about 5secs on my system.

I suggest you free up some disk space.  Boot to a Live CD or gparted CD if you have to.

---

### Post by the_nomad on 2007-12-30
i'm now on LiveCD and gparted seems to do the same...it scans devices for like 10 minutes...
by the way, might it be because i have like 250GB and like 7 partitions...?

---

### Post by nick_h on 2007-12-30
You have just one 250GB disk with 7 partitions?  I would expect it to scan in seconds not minutes.

Does fdisk work?
```
sudo fdisk -l
```

---

### Post by the_nomad on 2007-12-30
i haven't tried yet ... im now on windows, i have resized the ext2 partition and now logout screen (you know - logout, shudown, reboot screen) appears but there's now way i can do anything about firefox! i tried to complete remove it and remove its dependencies but it stopped since it doesn't find i dont know what file ... still, in terminal i get the same error.

---

### Post by the_nomad on 2007-12-30
anyone..? please... ? :(

---

### Post by nick_h on 2007-12-30
So you now have free disk space and your only problem is that firefox core dumps when you try to start it?

Have you tried reinstalling firefox?  You can do this from Synaptic.

---

