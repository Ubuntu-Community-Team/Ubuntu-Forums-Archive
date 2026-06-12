---
title: "Installation and partition issues"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-09-30
I am trying to install ubuntu but right now i have my hd in one partition for windows XP.  I boot ubuntu for the cd and then try to install.  it give me the option to resize my partition which i try to do and that it just size there was an error writing to the storage device.  I defraged my hd before i tried this and that did not help.  anyone know why else this might happen?

---

### Post by n3tfury on 2007-09-30
burn the gparted iso to cd and use that.  i've had pretty lame results using the built-in partitioner.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by bobplano on 2007-09-30
even better is the system rescue cd 'cause it can do more.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by RyanZec on 2007-09-30
I tried gparter and when it was trying to partition it failed.  error on trying to resize teh silesystem or something like that, am i out of luck?

---

### Post by n3tfury on 2007-09-30
> **RyanZec said:**
> I tried gparter and when it was trying to partition it failed.  error on trying to resize teh silesystem or something like that, am i out of luck?

you'll need to put the exact error in here for someone to help you out a bit more.

---

### Post by n3tfury on 2007-09-30
> **bobplano said:**
> even better is the system rescue cd 'cause it can do more.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

define "do more" for his situation.  it's still using gparted.  is there some other tool within there that he should be using to troubleshoot his issue?

---

### Post by RyanZec on 2007-09-30
I am going to try system resuce and if that fails i will get back to you guys on the exact errors.

---

### Post by RyanZec on 2007-09-30
This is the output:

Calibrate /dev/sda1 [OK]
Calculate new pize and position [OK]
Check File System [OK]
Shrink File System [ERROR]
Check File System [OK]
Grow File System to fill new partition [ERROR]

This is all the information i could get.

---

### Post by bobplano on 2007-09-30
> **n3tfury said:**
> define "do more" for his situation.  it's still using gparted.  is there some other tool within there that he should be using to troubleshoot his issue?

i meant that it had more things you could use for system rescue. yes for his situation there's not much difference

---

### Post by RyanZec on 2007-09-30
i guess I will just format my hd and install windows, only thing i currently need working in WoW, I am getting a new computer with vista in about 2 weeks.

---

