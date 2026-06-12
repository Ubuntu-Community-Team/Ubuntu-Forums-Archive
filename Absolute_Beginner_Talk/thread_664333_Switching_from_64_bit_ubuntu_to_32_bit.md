---
title: "Switching from 64 bit ubuntu to 32 bit"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-01-11
I want to switch my architecture from 64 bit to 32 bit by reformatting the partition, but before I do so, I need to find out which partition ubuntu is currently on. How can I detect the partition of my current installation?

---

### Post by Amstell on 2008-01-11
check gparted....that will list your partitions.

---

### Post by meindian523 on 2008-01-11
To detect the partition on which linux is installed:

In terminal:
```

fdisk -l
```

That's a small "L",not a 1.The partitions which have ext3 as their filesystem are your Linux partitions.

@Amstell

I doubt Linux installations come with GParted installed.

---

### Post by anothrguitarist on 2008-01-11
I'll try it out right now, thanks.

---

### Post by anothrguitarist on 2008-01-11
Hmm, nothing is displayed when I send the command

fdisk -l 

Do I need to turn echo on or log in as an admin?


EDIT: Resizing my existing ubungtu partition by 100% wouldn't cause problems would it?

---

### Post by meindian523 on 2008-01-11
oops,sorry you need sudo before that command.

edit:
> 
EDIT: Resizing my existing ubungtu partition by 100% wouldn't cause problems would it?

Meaning exactly what do you want to do?You want to use your entire HDD for Ubuntu?

---

### Post by anothrguitarist on 2008-01-11
Right now, I'm dual booting with Windows XP, and I want to get rid of my old Linux partition and install Ubuntu with the 32 bit architecture.

---

### Post by meindian523 on 2008-01-11
But do you want Windows XP or not?
If you resize your Ubuntu partition into unallocated space,it wouldn't cause a problem,but if you have to delete a partition to expand the space,you will lose all data on the partition you delete.It's also preferable to do the resizing during the installation.

---

### Post by anothrguitarist on 2008-01-11
Sorry, I have a guitar in my hands right now, and I've been a bit brief. I want to keep my XP partition as is, and reformat my Linux partition.

---

### Post by meindian523 on 2008-01-11
Ok,then,just find out which partition is your C: and don't format that/delete it and when you install 32-bit Ubuntu,format the Linux partitions and give them the mountpoints you did earlier.Resize if you want but make sure you have backed up all data from the partition you intend to delete.

---

