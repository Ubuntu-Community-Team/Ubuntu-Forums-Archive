---
title: "How do I browse my windows files? and some more questions"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by broodijzer on 2006-01-08
I"m a windows 2000 user, and installed this linux on my computer. Everything seems to work well so far, and I'd like to browse my c:/ partition to find some music and pictures to mess around a bit. On my desktop I see hda 1, hda3 and some more of those, but I don't really understand them.

and when browsing these forums, I see those messages "command xx". where do I enter those commands? I assume applications>system tools>run as different user? but that seems kind of unlogical to me.

And last question, I'm dual booting with windows 2000, which works perfectly fine. But I messed up my first 4 or so Ubuntu installations due to a corrupt cd.
now it looks like this

ubuntu (current install)
ubuntu safe mode (...)
memtest (...)
ubuntu
safe
memtest
ubuntu
safe
memtest
..
..
..
windows 2000
how do I remove the corrupt installations? 
that's all for now.

---

### Post by aysiu on 2006-01-08
See the fourth link of my sig.

---

### Post by pbb on 2006-01-08
> **broodijzer]I"m a windows 2000 user, and installed this linux on my computer. Everything seems to work well so far, and I'd like to browse my c:/ partition to find some music and pictures to mess around a bit. On my desktop I see hda 1, hda3 and some more of those, but I don't really understand them.[/QUOTE]

Hoi Broodijzer,

Giving partitions letters like C, D, etc, is really a Microsoft-only technique, you won't find that in Linux. Here, your drives have labels like hda1, etc. HD stands for harddisk, A means it's the first physical harddisk (master on the primary IDE connector, if that says anything to you), and 1 means it's the first partition on that harddisk. So, it's a save bet that hda1 is "the partition formerly known as C" (TPFKAC  said:**
> and when browsing these forums, I see those messages "command xx". where do I enter those commands? I assume applications>system tools>run as different user? but that seems kind of unlogical to me.

Your suspicions are right, you're supposed to use Applications > Accessories > Terminal. This is comparable to the DOS-prompt under Windows.

[QUOTE=broodijzer]And last question, I'm dual booting with windows 2000, which works perfectly fine. But I messed up my first 4 or so Ubuntu installations due to a corrupt cd.
now it looks like this

ubuntu (current install)
ubuntu safe mode (...)
memtest (...)
ubuntu
safe
memtest
ubuntu
safe
memtest
..
..
..
windows 2000
how do I remove the corrupt installations? 
that's all for now.[/QUOTE]

I can't be a lot of help on that one since I'm also a newbie, but the solution might be to edit /boot/grub/menu.lst. This file can only be edited with "root" priveleges, so you need to enter:
```
sudo gedit /boot/grub/menu.lst
```
Please make a backup copy before editing, because messing up this file may leave your computer unbootable...

---

### Post by vruum on 2006-01-08
commands found on the forum should be entered into a terminal, my guess is that it can be found at applications>system tools>terminal or applications>system tools>gnome-terminal.
about the confusing boot menu. have you upgraded your system? or installed a different kernel (if you don't know, you probably haven't) ubuntu keeps an entry for every kernel found on your system, so when you update your kernel or install a different one without removing the old one, both appear in the menu.

---

