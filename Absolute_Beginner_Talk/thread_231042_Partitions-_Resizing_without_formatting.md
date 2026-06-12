---
title: "Partitions- Resizing without formatting?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by CBTF on 2006-08-06
I recently installed ubuntu in a desgnated 80 GB partition, and made my xp's partition 100gb. I would now like to take space from the windows partition an give more space to my ubuntu partition.

Is this possible? If it is, how would I do this?

---

### Post by louistan3 on 2006-08-06
> **CBTF said:**
> I recently installed ubuntu in a desgnated 80 GB partition, and made my xp's partition 100gb. I would now like to take space from the windows partition an give more space to my ubuntu partition.

Is this possible? If it is, how would I do this?

im not sure if gparted can do those.. im a newbie too and i knw that gparted can resize partitions.. i thnk you should give it a shot.. :)

---

### Post by sir_mud on 2006-08-06
I don't think gparted will cooperate very well with ntfs partitions. I'll scan the documentation real quick and get back to ya.

*edit*
Apparently gparted does, it uses ntfsresize which is well known for its reliability...
even so...make a backup before you resize

---

### Post by cantormath on 2006-08-06
> **CBTF said:**
> I recently installed ubuntu in a desgnated 80 GB partition, and made my xp's partition 100gb. I would now like to take space from the windows partition an give more space to my ubuntu partition.

Is this possible? If it is, how would I do this?

You can do it with gparted, or fdisk.  You make one smaller then the other bigger.

you can also mount and read or write to your windows partition with [ntfs-3g]("http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/").


fdisk is a terminal app, and gparted is a gui for gnome. fdisk should be installed, and you'll have to install gparted from the repositories.

---

### Post by CBTF on 2006-08-06
thank you. it took me ages to get ubuntu configured to my liking im hoping i wont have to do it all again.

edit:

re: post above- how would i do that? id like to use g parted(extreme newbie)

ed2: nvm, going to try the gparted live cd. 

thanks for all your replies =D>

---

