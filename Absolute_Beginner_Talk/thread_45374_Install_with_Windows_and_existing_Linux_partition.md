---
title: "Install with Windows and existing Linux partition?"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by kyotodude on 2005-06-29
I have a laptop with Windows XP and SuSE Linux (9.2 Pro) installed.  I haven't recieved my Ubuntu CD yet, but I wanted to see if I could use my existing Linux partitions (don't care about what happends to SuSE) to install (without eating Windows!!).

---

### Post by aysiu on 2005-06-29
Yes. You just specify that you want to install /root where your current SuSE is, and Ubuntu will install right over it without touching your Windows partition.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=kyotodude]I have a laptop with Windows XP and SuSE Linux (9.2 Pro) installed.  I haven't recieved my Ubuntu CD yet, but I wanted to see if I could use my existing Linux partitions (don't care about what happends to SuSE) to install (without eating Windows!!).[/QUOTE]


Yep...but don't use the default partitioning options.

---

### Post by SQFreak on 2005-06-30
[QUOTE=aysiu]Yes. You just specify that you want to install /root where your current SuSE is, and Ubuntu will install right over it without touching your Windows partition.[/QUOTE]
 Be careful that you select custom partitioning in the installer and I strongly suggest formatting all linux partitions except the /home partition if you've got one, or backing up the /home directory and reformatting all linux partitions. Linux distros - especially ones as different and Ubuntu (deb-based) and SuSE (RPM-based) tend to not get along terribly well.

---

