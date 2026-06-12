---
title: "Installing Ubuntu on Core 2 duo"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by fatalfurry on 2006-11-21
I recently built a new computer it is a c2d E6300 with a Intel DG965WH mobo. I downloaded the amd x86-64 version of 6.10 and it will not boot into the live cd. It will load the kernel and then start the load screen. On this screen everything is gray not orange.(kida weird) It will give me an error and not go into the live cd. I am wondering what am I doing wrong?

---

### Post by Velotix on 2006-11-21
I'd go into the rigamarole of why you should stick with 32-bit Ubuntu over 64-bit Ubuntu for now, but you probably have heard all about that already.

What I will tell you is that I'm currently using the 32-bit i386 build of Ubuntu 6.10 on my Core 2 Duo PC and have had no issues with the processor. You might want to check the 32-bit CD works as well before continuing.

If you're set on 64-bit, there are a couple of generic reasons why your disc isn't working: the CD wasn't burnt properly, or you're one of the many with graphics driver problems. Not that I know much, but I'd say you're erring on the duff CD side, personally.

---

### Post by fatalfurry on 2006-11-23
So I tried installing the 32bit version of dapper and it gives me an error,
     Pci:Failed to allocate mem resource #6:20000@900000000000 for 0000:0100.0

When I try to install 6.10 32 or 64 bit it gives me the error of 
BusyBox v1.1.3 (Demian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of build-in commands

/bin/sh:can't access tty; job contol turned off
(initramfs)
Then I can type some suff in but idk what to enter. 


I have herd that there are some issues with the 965 chipset that I am currently using. Is there any way to install ubuntu on my computer?

---

### Post by drtvasudevan on 2006-11-24
me too!
same problems same errors.

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
this has been my home page for more than a month now.
still nothing that will work for me.
perhaps you will be more fortunate

---

