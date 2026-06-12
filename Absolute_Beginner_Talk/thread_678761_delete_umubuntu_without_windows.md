---
title: "delete umubuntu without windows"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by tinosa on 2008-01-26
I deleted my windows partition and installed umbuntu ( I'm experimenting with an old computer),
 I would like to set up a dual boot with windows now, but can't access my windows install cd.

My guess is that the grub that installed with umbunu is preventing this.
How can I clear my hard drive so I can get a fresh start ?(windows first then umbuntu)

---

### Post by Medieval_Creations on 2008-01-26
I'm not quite sure what you mean by can't access your Windows disk?  If you mean trying to launch it while in Ubuntu, that won't work.  If you mean that the PC won't boot to your windows CD then there are other problems with either the disc or why the PC won't boot to CD.

Just a word of advice, if you want a dual boot (XP & Ubuntu), you are probably going to want to repartition your hard drive and reinstall XP on the first partition and then reintsall Ubuntu onto the second.  The reason being is that when you reinstall XP after unbuntu XP overwrites the MBR (Master Boot Record) and will only then boot you into XP and not prompt you if you want to load Ubuntu.

There are other ways around this, but this is probably one of the easier ways that I've found that doesn't involve editing files in either OS.

---

### Post by gvartser on 2008-01-26
umbuntu??

:)
/g

---

### Post by Paul820 on 2008-01-26
> **gvartser said:**
> umbuntu??

:)
/g

Yeah, it's similar to umbongo :)

---

### Post by spydon on 2008-01-26
Check you BIOS and see if cd/dvd is before hdd in the boot order, i'm quite sure that grub doesn't change anything in your boot options.

---

### Post by tinosa on 2008-01-26
Thanks much, it was the bios. don't know how it changed but problem solved.  :)

---

