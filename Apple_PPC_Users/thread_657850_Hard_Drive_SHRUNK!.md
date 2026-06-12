---
title: "Hard Drive SHRUNK!?"
date: 2008-01-04
forum: Apple PPC Users
---

### Post by iLinuxred on 2008-01-04
UM... I am very new at this. I loaded fiesty onto my iMac g3. it is red and has a 10 gigabyte hard rive. It says in the drive thing that it is really only 6.5 gigs. Thats not right... is it? the system cant take more than 700 megabytes right?

---

### Post by perlluver on 2008-01-04
Also swap space, depending on the amount of memory.  You will not see the swap space being used.  Mine is 2GB for swap.

---

### Post by iLinuxred on 2008-01-04
what? what is swap space. Im very new at this.

---

### Post by iLinuxred on 2008-01-04
is it possible that the installer did not delete everything from the os9?

---

### Post by perlluver on 2008-01-04
> **iLinuxred said:**
> what? what is swap space. Im very new at this.

Swap space is used, when your memory is all used up.  Like a page file.  Whenever all your memory is used swap space kicks in as a backup memory.  I have 1GB of memory, and 2GB of swap space.

Web Definition of swap space :Swap Space
Area on a hard disk where processes go if out of physical memory. It is part of the virtual memory system of all Unixes, allowing for more process memory than physical memory, if needed

---

### Post by perlluver on 2008-01-04
> **iLinuxred said:**
> is it possible that the installer did not delete everything from the os9?

If you chose to do a fresh install, where is said will use whole hard disk, then no.  If you used the largest available space then yes.

---

### Post by iLinuxred on 2008-01-04
oh...yeah. I know it as virtual memory.

now I cant remember if it was a clean install... I guess ill just do it again.

---

### Post by tht00 on 2008-01-04
Pull up a terminal and put in:
sudo fdisk -l

This will list all of your partitions and hard drive information.  Post what it spits out.

---

