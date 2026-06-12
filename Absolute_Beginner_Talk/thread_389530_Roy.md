---
title: "Roy"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by serenety on 2007-03-20
Help: I am frustrated with Ubuntu. I cannot get it to work and I have tried everything I know. I have knowledge of computers. However, I do not want this system on my computer any more. Can someone tell me how to remove it?

---

### Post by alienexplorers on 2007-03-20
Format your drive and load Windows or whatever.  It's that easy..

---

### Post by serenety on 2007-03-20
> **alienexplorers said:**
> Format your drive and load Windows or whatever.  It's that easy..

I know that but I do not want to format. This is a duel boot and I have windows installed and right now I cannot back up my windows operating system and files.

---

### Post by alienexplorers on 2007-03-21
Boot with the livecd and run gparted.  Remove the partition you don't want and make the unused space available for either data in windows or another linux distro.

---

### Post by cowlip on 2007-03-21
after you resize it, put in a windows cd, go to the recovery console and type "fdisk /mbr" or "fixmbr" to remove GRUB.

---

