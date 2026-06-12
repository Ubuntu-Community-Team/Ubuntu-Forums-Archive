---
title: "fstab and mounting partition"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by thornate on 2007-11-05
I have a fat32 partition that I'm using to save all my files in both Ubuntu and Windows. I added it to fstab so that it would automount but it's only giving me Access Permission, not full RW. The line as I have it is:
UUID=4712-AB28	/media/OS-SHARED	vfat	defaults,rw,users	0	2

I've also tried it with just 'defaults' and pretty much every other combination. 

So what options should I be using? Also, do I need that '2' at the end; wouldn't it slow down booting if it has to check that drive every time?

---

### Post by Steve1961 on 2007-11-05
See this link:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by thornate on 2007-11-05
Sorry, maybe I wasn't clear enough. This is not my Windows partition. This is a seperate partition (on a completely different disk) that I want to use in both Windows and Ubuntu to save files.

---

### Post by Steve1961 on 2007-11-06
Scroll down - you'll see an entry for a fat32 partition

---

### Post by thornate on 2007-11-11
EDIT: It's working now. Wish I knew why.

Thanks.

---

