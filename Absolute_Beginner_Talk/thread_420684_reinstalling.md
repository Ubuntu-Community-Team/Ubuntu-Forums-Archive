---
title: "reinstalling?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-04-23
so i totally destroyed my ubuntu.
i really want to reinstall it but when i do it wont put it on the same partition, so i figure i gotta remove it.
i really need help with this; as if you were talking to a child.
please no "i can help you fix the problem"
ive been trying for a few days
thank you

---

### Post by LaurelLynn on 2007-04-23
Dear thelegionnaire,

When you install some versions it has trouble installing on to an existing partition (it did for me). The fix I found for that on the forum  is to choose ¨manual partitioning¨.  Then delete the original, then recreate it. That usually seems to make Ubuntu happy.

---

### Post by crispy_420 on 2007-04-23
Why not just erase the whole disc (or partition) and start from there? You do want to start from scratch right?

There are several tools to erase. You could use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") or [Darik's Boot and Nuke]("http://dban.sourceforge.net/"). They both free options.

Is that what you are looking for?

---

### Post by thelegionnaire on 2007-04-24
guess you didnt see the part where it said "talking to a child" :)
if i delete the partition, and reinstall, do i have to do anything with grub?
wont it show 2 ubuntu's


ill try the "manual" suggestion; im on a work computer right now

thanks for the advice

---

### Post by LaurelLynn on 2007-04-24
If you are reinstalling, it will put a new copy of GRUB at the beginning of the drive. Then it will create a new /boot/grub/menu.lst during the installation and add entries for every os it finds on all of your partitions (even windows).

---

### Post by crispy_420 on 2007-04-26
If you reformat the entire drive, all is gone. That includes grub.

Laurel is it just me or do you seem to find the posts to post on as me?

---

### Post by byen on 2007-04-26
> **crispy_420 said:**
> If you reformat the entire drive, all is gone. That includes grub
Ditto! When you reinstall ubuntu, the entire drive gets cleaned and a fresh install takes its place. This includes the grub. Just do what you did when you first installed Ubuntu and you should be ok. Goodluck.

---

