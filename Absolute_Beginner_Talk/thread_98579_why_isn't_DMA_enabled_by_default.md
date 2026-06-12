---
title: "why isn't DMA enabled by default?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by chiisu on 2005-12-03
:confused:

---

### Post by doitashimashite on 2005-12-03
I wouldn't know, but it's simple to enable DMA on certain drives:

sudo gedit /etc/hdparm.conf

and add the lines (in this example for a primary slave drive):

/dev/hdb {
dma = on
}

---

### Post by tseliot on 2005-12-04
DMA is not enabled by default because if a device (old hardisks, etc.) doesn't support it you won't be able to access that device at all.

You can enable DMA hdparm as suggested by the fellow above.

OR

Recompile your kernel and disable the option "Enable DMA only for disks" (or sth like that)

---

### Post by Gray. on 2005-12-04
For any easy graphical way to enable DMA along with a whole host of other things is to use [Automatix]("http://ubuntuforums.org/showthread.php?t=66563").

---

### Post by towsonu2003 on 2005-12-04
[QUOTE=tseliot]DMA is not enabled by default because if a device (old hardisks, etc.) doesn't support it you won't be able to access that device at all.
[/QUOTE]

here's my newbie question: would enabling DMA on a drive not supporting it break that drive/other hardware?
thanks

---

### Post by tseliot on 2005-12-05
[QUOTE=towsonu2003]here's my newbie question: would enabling DMA on a drive not supporting it break that drive/other hardware?
thanks[/QUOTE]
No, it won't break anything. You just won't be able to access the device (only the oldest devices have problems with DMA) if you use a kernel which has DMA enabled. But if you boot in another kernel or disable DMA through hdparm you will be able to access the device again (without any damages).

---

