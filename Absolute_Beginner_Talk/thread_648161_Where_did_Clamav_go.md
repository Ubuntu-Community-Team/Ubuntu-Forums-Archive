---
title: "Where did Clamav go"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-23
Having downloaded Clamav from Synaptic Packet manager I'm now unable to find it on my computer. Where should I look for it please.

---

### Post by Sef on 2007-12-23
Systems > Preferences > Main Menu > Accessories (click on the box next to clamav)

---

### Post by a.v.l on 2007-12-23
> **Sef said:**
> Systems > Preferences > Main Menu > Accessories (click on the box next to clamav)

Clamav doesn't appear in  Accessories as instructed above.  When I check in Synaptic Packet Manager,  Clamav is installed. How should I deal with this situation please?

---

### Post by frank002 on 2007-12-23
Did you also install ClamTK? It is the graphical front end for ClamAv.

---

### Post by seventhc on 2007-12-23
If you ididnt install ClamTK but installed a clamAV then you can open a terminal and type in clamscan -r /home  That will scan users home directories .
but have a look here 
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

sudo freshclam
to update it.

---

### Post by a.v.l on 2007-12-24
Thanks everyone, I'll check  on your suggetions after work this evening.

---

### Post by a.v.l on 2007-12-27
> **frank002 said:**
> Did you also install ClamTK? It is the graphical front end for ClamAv.

Thanks, installing ClamTK did it.

---

