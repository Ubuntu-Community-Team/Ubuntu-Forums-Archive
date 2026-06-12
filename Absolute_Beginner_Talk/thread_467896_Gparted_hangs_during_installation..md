---
title: "Gparted hangs during installation."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by david.rollins2 on 2007-06-08
I am trying to make the switch from Windows to Linux - Ubuntu 7.04, like thousands of other that are tired of their Windows machine. But it is proving to be a more difficult task for me to do than I expected. 
The Ubuntu CD loads fine. But the install stalls when Gparted tries to scan my hard disk. Last night I downloaded the Gparted LiveCD and was able to boot into Gparted, view the disk and even set up a swap file. But going back to Ubuntu, Gprated still hangs. Even if I try to run Gparted by itself within Ubuntu, it hangs. Does anyone have a clue to what could be wrong?

---

### Post by brim4brim on 2007-06-08
You can try using the Alternate CD or Server CD to install Ubuntu.  Its kind of hard to tell whats wrong if there are no messages or errors coming up.  Post the specs of your machine and maybe someone will know of a known issue.

---

### Post by david.rollins2 on 2007-06-09
I found out what it was, Ubuntu was trying to scan my removable media slots as SCSI devices. They are SD, MS, CF and SM memory slots. I'm not sure why Ubuntu would try to read those slots as hard disks though. Maybe its a bug?

---

