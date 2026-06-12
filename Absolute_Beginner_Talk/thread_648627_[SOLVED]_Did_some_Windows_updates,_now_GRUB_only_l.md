---
title: "[SOLVED] Did some Windows updates, now GRUB only loads Gutsy"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by flehnerz on 2007-12-23
So I or should I say Windows Vista (Virus) took the liberty of installing service pack 1 and when I restarted, I lost my ability to boot into Virus. Grub does not load at all. Ubuntu simply boots like if it were the only operating system on my machine. Any ideas is to how and why Micro$oft screwed up my machine this time?

---

### Post by wormser on 2007-12-23
It sounds to me like Vista is telling you to use Ubuntu.

You need to fix GRUB.  The first 2 posts in this [thread]("http://ubuntuforums.org/showthread.php?t=24113") have directions to fix it.

---

### Post by shareMenaPeace on 2007-12-23
If this fails you can also try supergrub.forjamari.linex.org/  a grub boot disc

---

### Post by flehnerz on 2007-12-23
> **wormser said:**
> It sounds to me like Vista is telling you to use Ubuntu.

You need to fix GRUB.  The first 2 posts in this [thread]("http://ubuntuforums.org/showthread.php?t=24113") have directions to fix it.

This won't help me right now. I'm traveling around in Mexico. I don't have a live CD nor the resources to get a blank CD. I guess I'll have to wait until I return home.
I'm going to work on installing a distro to a USB drive and then I'll follow the thread.

---

### Post by meierfra on 2007-12-23
Since you can boot into  ubuntu, you don't need a LiveCD to fix Grub . Open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by flehnerz on 2007-12-23
Got it, live USB, very handy if you ask me (and if your BIOS supports USB boot).

---

