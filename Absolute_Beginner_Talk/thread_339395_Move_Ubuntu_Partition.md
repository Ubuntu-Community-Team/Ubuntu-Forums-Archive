---
title: "Move Ubuntu Partition?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-15
Is it possible to completely move my ubuntu partition? It's the 2nd of two on my disk right now. And I've finally gotten up the courage to completely remove my windows partition. I know I can resize my ubuntu partition, but can i completely move it?

---

### Post by bodhi.zazen on 2007-01-15
Yes.

Move it from a live CD, wither the Ubuntu Desktop or the GParted CD (which is worth the download).

You will need to update /etc/fstab and /boot/grub/menu.lst

**[color=red]FROM THE LIVE CD[/color]**

or your system will not boot.

See this thread for basic instructions:

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

### Post by rj686 on 2007-01-15
How do i copy the partition? From within gparted, or on commandline?

---

### Post by bodhi.zazen on 2007-01-15
From within Gparted ...

There is a set of copy/paste/move partition buttons :p

---

### Post by rj686 on 2007-01-15
> **bodhi.zazen said:**
> From within Gparted ...

There is a set of copy/paste/move partition buttons :p

Yeah I used those at first and tried copying to ext3 from reisfer FS and my used space was 4x the size lol. I missed the line where you said same filesystem. I tried it again with same filesystem and it worked fine.

---

