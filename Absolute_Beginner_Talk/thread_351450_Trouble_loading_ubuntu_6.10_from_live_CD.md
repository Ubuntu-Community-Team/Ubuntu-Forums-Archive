---
title: "Trouble loading ubuntu 6.10 from live CD"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by schnitzel on 2007-02-01
I'm attempting to install ubuntu 6.10 from a live CD and can't get to the first screen. Instead, I get a DOS screen that looks like it's booting from the CD ("...Starting Caldera DR-DOS...") and continues with the following:

"
Device Name: MSCD001
Number of Drives: 1

...

Usage: Fat32.exe [-wl] [-u]
         -wl  - Without LFN support
         -u   - Unload driver

run-time error R6001
-null pointer assignment
NTFS Filesystem Driver for DR-DOS

"

Ideas?

---

### Post by meng on 2007-02-01
You burned the CD wrongly, this is what happens when you "Burn bootable disk" in Nero or similar program. Look here for how to burn a CD properly.
[www.psychocats.net/ubuntu/iso](www.psychocats.net/ubuntu/iso)

---

### Post by schnitzel on 2007-02-02
Yes, I used Nero. Thanks, I'll give that a try.

---

### Post by schnitzel on 2007-02-05
Follow up -
I did get it to work following those instructions; but for any other new users out there that may be reading this, I did have to install .NET in order to download and run the CD burning software. Also, I had several 'bad' burns and was sucessful only when burning at 1x.

---

