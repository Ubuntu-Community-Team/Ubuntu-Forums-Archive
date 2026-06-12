---
title: "Gnome Partition Editor Problems"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by thomasfedb on 2007-07-10
I was trying to shrink my windows NTFS Partition by 20 gigs in Gnome Partition Editor and everything went well untill i clicked on the apply button (scarry) and everything seemed to be working and then Gnome Partition Edito vanithed from the screen. I'v tried 3 more times and it always just vanishes. i'm using a 7.04 Live CD because the installer dosn't give me the option to resize my windows partition.

Thankyou in advance for any help !

---

### Post by Moop on 2007-07-10
Did you check that live cd for errors?

---

### Post by louieb on 2007-07-10
Did you prep your NTFS partition for shrinking? Defrag and other stuff. Nice what to look for here [Creating a Dual-Boot Windows XP and Ubuntu Laptop]("http://www.linuxdevcenter.com/lpt/a/6554") also some gnu defrag software [JkDefrag: A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")

---

### Post by thomasfedb on 2007-07-11
Thank you very much i have defraged and i tried again and i gave me an error saying my NTFS journal was not correct so i'll fix that and try again (CHKDSK @ boot, i think)

Thank you very much

---

### Post by macogw on 2007-07-11
chksdk /f
is probably the command you want

---

