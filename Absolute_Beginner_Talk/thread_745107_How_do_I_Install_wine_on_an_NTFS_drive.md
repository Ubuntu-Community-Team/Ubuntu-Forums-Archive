---
title: "How do I Install wine on an NTFS drive?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by CapsLardmin on 2008-04-04
I want to install wine on a larger disk. I have installed kubuntu with wubi so I only have 30 gb of space.

How do I do this?

---

### Post by Oldsoldier2003 on 2008-04-04
> **CapsLardmin said:**
> I want to install wine on a larger disk. I have installed kubuntu with wubi so I only have 30 gb of space.

How do I do this?

To be absolutely honest, Ii would counsel on repartitioning your drives to make room rather than attempting to install Wine on a NTFS partition. Wine by default sets itself up in your /home/<user>/.wine directory NTFS permissions will probably create havoc with the operation of wine, and putting you /home on a NTFS partition will create login problems that will ultimately end up in having to reinstall Ubuntu.

---

### Post by Slushdoot on 2008-04-04
You might be able to set in your fstab that the system mount the NTFS partition in /home/capslardmin/.wine

I don't know if i8t being a Wubi installation would change this.  I know it'd definitely work if it were a traditional installation.

---

