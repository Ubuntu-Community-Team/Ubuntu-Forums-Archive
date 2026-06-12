---
title: "defrag style program?check disk?fragmentation?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-28
hi basically azureus has problems resuming from another hard drive after a new format of my ubuntu installation drive... it says something about checkdisc etc?is there any kind of program or command i can run like it uses on boot up to smooth out the errors and sort my discs out as checking the downloaded files is SO slow now:( and errors:(
cheers

---

### Post by [S|G] on 2007-04-28
It is unlikely your ext3 will become fragmented under normal usage, so there's no real need to defragment your hard drive. You can check the filesystem for errors using the fsck tool, but you'd need to boot into recovery mode and do that with your filesystem unmounted. 

Usually the system will detect if there is any problems and do it on its own when you boot it (it also does that every 30 times you mount the filesystem automatically).

---

