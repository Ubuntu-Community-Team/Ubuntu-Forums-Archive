---
title: "Unattended backup script?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by bhold on 2008-03-10
Currently I back up my system by running a script to create a tar.gz file, then a separate manual step running gnome-baker to write the tar.gz to dvd.

I would like to automate this under cron, and just always keep a dvd in the device and have the backup run and write to dvd once per week. 

Anyone have a similar script I could take a look at?

---

### Post by njparton on 2008-03-11
Can all the steps you require be performed from a terminal?

If so write a bash script (google it for tutorials).  I have a bash script called by cron that runs a series of rsync commands on an hourly basis. Remember to run it from sudo's cron, not your own.

If you need more than terminal commands then you'll probably need to write something in python (or similar) and then you're into the realms of programming..

---

### Post by hyper_ch on 2008-03-11
I wrote my own little script that does that... making backups every 6h and keeping them for 90 days and once a day I mirror the backup to my computer at my parents' home just to have a decentralized version also.

---

