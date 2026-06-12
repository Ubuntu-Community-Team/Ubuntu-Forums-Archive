---
title: "over wrote XP with Ubuntu = problems"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by saxuntu on 2007-07-05
I used Gparted to on the ubuntu LiveCD and formated the ntfs section to ext3 and then used the LiveCD to install and have incountered problems:

1) nVidia geforce2 MX works but graphics slow down and get "jerky"

2) FIle system failure on boot up. But when I hit ctrl-d it boots everything appears to work fine. I would just like it to boot normally.

3) Suuspend and Hibernate - the monitor will turn on but all i get is a black screen.

---

### Post by foxmulder881 on 2007-07-05
> **saxuntu said:**
> 1) nVidia geforce2 MX works but graphics slow down and get "jerky"

Have you installed the x.org accelerated drivers?

> **saxuntu said:**
> 2) FIle system failure on boot up. But when I hit ctrl-d it boots everything appears to work fine. I would just like it to boot normally.

Funny enough, I just had this same problem this week. How to fix it, I have no idea.
I got fed up with Feisty. This was the third time that it has stuffed up on me since official release.
I uninstalled it and installed Freespire until I can reinstall Dapper.

> **saxuntu said:**
> 3) Suuspend and Hibernate - the monitor will turn on but all i get is a black screen.

Is this putting your computer into suspend or rebooting after suspend? Need more info.

---

### Post by saxuntu on 2007-07-05
yes its the legacy one - i used synaptic
if it helps with the boot problem the log that was generated spit out:
Log of fsck -C -R -A -a 
Thu Jul  5 20:08:15 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda3: 3271 files, 1539243/2893297 clusters
fsck.ext3: Unable to resolve 'UUID=4c4d2110-d19e-4e0b-9c34-3b019d3d42a9'

fsck died with exit status 8

Thu Jul  5 20:08:19 2007
----------------

After it goes into suspend when i try to reactivate the computer.

---

### Post by foxmulder881 on 2007-07-05
I had the same issue also with the suspend. My PC tower appeared to be working but nothing was on the monitor. Turning monitor off and back on also didn't help.
This tells me it's a vid card driver issue with certain cards.

---

### Post by enopepsoo on 2007-07-05
> >  over wrote XP with Ubuntu

congrulations! :)

---

