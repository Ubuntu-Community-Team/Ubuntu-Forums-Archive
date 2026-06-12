---
title: "[SOLVED] Computer freezes while mounting root file system"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by AaronJ on 2007-10-12
Hi,

Im trying to use the Ubuntu 6.06 1 i3 live cd on my thinkpad , but when the computer is trying to mount the root file system the computer freezes. I have retried this a number of times, this message comes when I  press alt-F1 as suggested here in the forums.

**"bug: soft lockup detected on cpu#0"**

Anybody know what the problem is? :(

Im using a burned cd, but the cd works fine on my desktop computer.

Should I use other forms of Ubuntu instead?

[B]My computer:
IBM Thinkpad R30
Intel Celeron processor 900 Mhz
256 MB  Ram
20GB hard disk[/B]

---

### Post by ddrichardson on 2007-10-12
Do you have a wireless card and if so what type is it? It appears in most cases to be related to ipw3945 module and kill switches, but I believe it went away with Fiesty - can you try a Fiesty CD?

---

### Post by Pumalite on 2007-10-12
256 MB RAM> Xubuntu Alternate CD:[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
You could mount a Live CD making a 500 MB /swap ahead of time, but if booted and installed, system would be kind of slow in your computer.

---

### Post by AaronJ on 2007-10-12
@ ddrichardson: yes I have a wireless card but it wasnt actually in the computer when I booted it. It is a Proxim 802.11b pc-card. 

@Pumalite: Im sorry but I dont really understand this :confused: " make a 500 MB /swap ahead of time"

ddrichardson, I can dl Feisty fawn and see if that works but if I understand Pumalite correctly Feist Fawn would be slow. Would it be slower than XP already is on that computer?b

---

### Post by Pumalite on 2007-10-12
If you insist. Use Gparted and in the partition you are going to use to install Ubuntu, make a /swap partition. Then boot your Live CD. It should work.

---

### Post by Pumalite on 2007-10-12
If you insist. Use Gparted and in the partition you are going to use to install Ubuntu, make a /swap partition. Then boot your Live CD. It should work.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)

[http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)

---

### Post by ddrichardson on 2007-10-13
> **AaronJ said:**
> ddrichardson, I can dl Feisty fawn and see if that works but if I understand Pumalite correctly Feist Fawn would be slow. Would it be slower than XP already is on that computer?bYou can use a Xubuntu Fawn CD.

---

### Post by AaronJ on 2007-10-14
Xubuntu worked with some cajoling. Thanks guys for your input.

---

