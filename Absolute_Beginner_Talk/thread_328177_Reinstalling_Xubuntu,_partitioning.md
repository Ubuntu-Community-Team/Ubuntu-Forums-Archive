---
title: "Reinstalling Xubuntu, partitioning?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-30
I'm reinstalling Xubuntu on my laptop one final time, in an effort to fix up my Xubuntu (It's kind of messed up from mis-installing some apps) and to create a /home partition!

I have an 80 GB HD, and I need your opinions on how I should split it. Also, should I make partitions for /boot and other / folders?

---

### Post by shanepardue on 2006-12-30
I just do two partitions...one for apps and one for files. that way you can do whatever to your install, but you still got your files. / for apps and /home for files.

edit: can't forget swap! i do a gig

---

### Post by taurus on 2006-12-30
Personally, I would do something like

/dev/hda1 -- /boot (100MB)
/dev/hda2 -- / (10GB)
/dev/hda3 -- swap (1GB)
/dev/hda4 -- /home (whatever left)

Then, when you decide to reinstall Edgy again or Feisty later on, you can mount /dev/hda4 to /home but do not format it.  All your personal settings will still be there...

---

### Post by Pobega on 2006-12-30
Well I'm running from the Xubuntu LiveCD right now, and I can't figure out how to edit the partition table. My current partitions are /dev/sda1, /dev/sda2 and /dev/sda5 (sda5 is in sda2).

**Edit:** This is my first time partitioning anything, so any help would be appreciated.

---

### Post by taurus on 2006-12-30
When I installed Xubuntu on my laptop, I used the alternate CD so I am not sure if Xubuntu LieCD comes with gparted.  If it does, you can use it to resize partitioning your hard.  Otherwise, you can use the manual editing partition with the alternate CD when you get to that part.  Erase all the partitions and start it from the beginning...

---

### Post by Pobega on 2006-12-30
Yeah, but I really have no idea what is what. ext3 and whatnot is very confusing to me. As I said, I've never partitioned anything before.

---

### Post by taurus on 2006-12-30
For Linux, you want to use ext3 filesystem.  For swap, use swap.

---

