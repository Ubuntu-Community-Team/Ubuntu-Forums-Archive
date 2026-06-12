---
title: "How can I point ClamAV or Avast windows partition"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by babacan on 2007-08-10
Hi
I have downloaded 2 antivirus program which are avast and ClamAV.
When I type clamscan or avast , it directly scans my my Home directory but I want them to scan my Windows partition which is shown as "SDA1" at file directy to the partition.

---

### Post by Hospadar on 2007-08-10
Well your windows partition is going to be mounted at /media/sda1, so that's what  you'll be wanting to scan.

Try ```
clamscan /media/sda1
``` that should do the trick.

---

### Post by babacan on 2007-08-10
ah thanks alot!

---

