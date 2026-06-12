---
title: "ubuntu cant detect my partitions"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Sprogg2001 on 2006-09-11
After a failed ubuntu installation I wanted to try again with Xubuntu only to find that the live cd's on both distros cant install because they cannot find my partitions, even gparted cant detect any hard drives its all gone to :-# !!!

I can get into grub on the xubuntu live cd but have no idea what Im doing, is there anyway I can nuke my system clean and start afresh

all I want is a simple install of xubuntu oh and I have no idea what my hard drive is called theres only one so it might be hda0 or it could be called blue betty peekaboo for all I know thats why I come to the experts for help!

so please save me from this hell.

---

### Post by kidders on 2006-09-11
Not being able to detect your hard drives is ... well ... bad :-(

Are you certain you haven't tinkered with anything in your BIOS settings that might be hiding them? What kind of drives are they?

---

### Post by Najand on 2006-09-11
If you can boot using any of ubuntu medias, can you open a terminal (if graphical mode fails, push Ctrl+Alt+F1 and enter the text mode) .. 
Running:
```
fdisk -l
```
can show your harddisk. Can you write it down here... Then I can tell you how to handle it...

---

