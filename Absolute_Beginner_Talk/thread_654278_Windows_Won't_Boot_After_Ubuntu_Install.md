---
title: "Windows Won't Boot After Ubuntu Install"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-12-30
I have had Windows XP for some time.  After a recent bug fix (which it turns out actually wasn't fixed yet), I decided to re-install Ubuntu.  I let Ubuntu resize the partition of WIndows.  After installation, Ubuntu boots fine, but I can't boot into Windows.

As I click  on Windows XP in GRUB, the Windows graphic appears, then a few seconds later I get a really quick flash of the blue screen of death and a restart.  It does not stay long enough to read.  This happened immediately after the Ubuntu install.

what should I do next?

---

### Post by tommytomthms5 on 2007-12-30
take a look to see if your data is still there if it is back up as much as you can and then try stuff from there

---

### Post by arvindenrique on 2007-12-30
uninstall xp and reinstall it . the problem will be fixed. backup your drivers

---

### Post by brandoncolorado on 2007-12-30
> **arvindenrique said:**
> uninstall xp and reinstall it . the problem will be fixed. backup your drivers

But if I do that, won't it install over Ubuntu?  Last I tried that, it forced me to reformat the whole disk.

---

### Post by penguinv on 2007-12-30
> **brandoncolorado said:**
> But if I do that, won't it install over Ubuntu?  Last I tried that, it forced me to reformat the whole disk.
[I]
"I don't know but I've been told"[/I] that one should choose REPAIR rather than REINSTALL and XP will not reformat your disk.

Myself, I have not been able to lay my hands on a simple Windows XP Pro install disk. I have only the (Euphemistically Named) Recovery disk. Using it means you recover nothing but XP and lose everything else. Kind of like a lobotomy.

---

### Post by fiddledd on 2007-12-31
I would boot into Ubuntu, backup all important data from the XP partition, then reboot with XP install disk and do a repair install. Although repair would be expected to leave your Documents intact it is Windows, which is why I'd backup first. it sounds like you are missing drivers that windows needs to load, that's what the repair install replaces.

---

### Post by brandoncolorado on 2007-12-31
Thanks for the help.

I got the problem fixed by running chkdsk.  Simple enough fix!

Thanks Ubuntu!


*I now have sound, wireless, and no problems*

---

