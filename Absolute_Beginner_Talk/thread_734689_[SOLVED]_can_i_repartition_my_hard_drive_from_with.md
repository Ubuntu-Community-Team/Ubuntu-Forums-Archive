---
title: "[SOLVED] can i repartition my hard drive from within damn small linux?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Calindae on 2008-03-24
Is there any way i can do this as i have no access to a cd burner...

---

### Post by smartboyathome on 2008-03-24
Install GParted and then you can.

---

### Post by tgalati4 on 2008-03-25
You can check the Damn Small Linux forums for hints on how to do it.  You can download a USB-boot floppy and put the ISO on a flash disk.  No CD needed.  From there, boot into DSL, open a terminal:

>sudo cfdisk /dev/hda

Proceed carefully.  Back up important data before making changes to the partition table.

---

