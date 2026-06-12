---
title: "HFS+ Partition Error &amp; Grub sigh..."
date: 2007-05-17
forum: Apple Intel Users
---

### Post by l0c0m0c0 on 2007-05-17
Hey guys I have used the Deadmoo image to put OSX on a partition that is on the same drive as my Ubuntu install.  All the files are on the partition, I can mount it browse etc..  When I try to boot it with Grub I get: 

> HFS+ Partition Error

Here is my menu.lst
> title		WindowZ XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=225ed343-3684-4eb2-860e-39ee20113430 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title 		OSX
rootnoverify		(hd0,2)
makeactive
chainloader 	 +1

Win and Ubuntu both boot fine.  Any ideas?

---

### Post by l0c0m0c0 on 2007-05-22
No one?

---

### Post by ronocdh on 2007-05-22
I had to Google "deadmoo," and having done that, I gather it's a hacked version of OS X meant to run on computers other than Intel Macs, is that correct? This forum is explicitly for users of the Intel Macs, and so I don't know how many here would be both able and willing to help you out in your predicament.

Feel free to go into more detail about the problem.

---

### Post by l0c0m0c0 on 2007-05-22
Ok nvm sorry.

---

