---
title: "How to upgrade kernel if not in package ?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by anewbie on 2006-11-05
I'm running edgy (6.10) which has kernel 2.6.17-10. I'd like to upgrade the kernel to 2.6.18 > 2.6.18-2 or 2.6.19 (I think rc4 just passed) to address some hardware issues. apt-cache search indicates that 2.6.17-10 is the latest..

Is there a standard method to upgrade the kernel in this situation? If i wait how long does it typically take for edgy to track a newer kernel ?

---

### Post by MasterOfDisaster on 2006-11-05
Not totally sure here, but I think that edgy will stick with the same kernel throughout it's lifespan, for stability reasons.  This way the Ubuntu community can release bug fixes and such.

If you need a more up-to-date kernel, I guess you would have to compile it yourself?  Never done this, so good luck.

---

### Post by anewbie on 2006-11-05
Anyone know of the 'standard' method to do this ??

---

### Post by tronica on 2006-11-05
just what you need

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by NeoLithium on 2006-11-05
[http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

This is a nice walkthrough for how to compile the 2.6.18 kernel; nice and easy.

---

### Post by anewbie on 2006-11-05
Ok thanks. That is exactly what I need. I'll give it a shot in a day or so.

---

### Post by Daveski on 2006-11-05
I have wondered what happens if you have your own compiled kernel in ubuntu, and an official kernel package is released. Do you automatically get the official kernel as part of the system update downloads? Does this replace your custom kernel, or do they both appear in the Grub menu?

---

### Post by anewbie on 2006-11-08
I wonder tooo.

---

### Post by anewbie on 2006-11-17
Arrggg. I tried building the kernel 2.6.18.2 as per suggested above but it doesn't work. It dies here:

Nov 17 18:33:54 pc1 kernel: [17179582.472000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[58]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]

---
Well that is the last thing it prints then hangs. With 2.6.17-10 (which works) the next line is:

md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
--
Any suggestions how to debug this ?

---

### Post by linuxnewbie946 on 2006-11-18
It looks like you forgot to check something that your hardware needs to boot. Try booting into your old kernel and type make oldconfig before typing make xconfig. This will check anything your current kernel needs to boot.

---

### Post by anewbie on 2006-11-18
That's probably the problem since this is a p965 board. I was esp concern about the jmb363 but didnt' see it explicitly listed. 

Anyways - I tried your suggestion - no cigar. Still won't boot. Guess I'm stuck with 2.16.17-10 until a new kernel becomes availabe via ubuntu - and even that one might not work.

---

