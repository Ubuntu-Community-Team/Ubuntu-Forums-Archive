---
title: "PPC vs i686"
date: 2006-08-14
forum: Apple PPC Users
---

### Post by Socratez on 2006-08-14
I am going to buy myself a older dedicated protable Ubuntu machine in the next few weeks. I have been throwing around the idea of buying a MAC G3 vs a P3 but I am curious which one is going to perform better. I would imagine either will be a 600-800MHz machine with 256-512MB of RAM. Would getting a Macbook give me a performance boost? Should i just stick with Intel? 

Soc

---

### Post by iamhugeinjapan on 2006-08-14
I use Ubuntu on x86 and ppc platforms. It really depends on what you want to use it for. The higher specs the better but if its similar, it can come down to how good the motherboard is etc.

If you just want to do basic websites, IM and a bit of word processing. Then ppc will do just fine. However if you're wanting to do a lot of websites with flash/java components or fancy codecs then you'll struggle a bit.

The ppc does just fine for most of my laptop needs. I couldn't cope with a ppc main desktop though. If you're getting a slower laptop, I highly recommend using Xubuntu. It leaves me with so much more RAM free.

---

### Post by Socratez on 2006-08-14
Thanks for the info. I mainly want it for a portable audio workstation. I want to be able to record and edit audio as well as play through stero systems. I figured where MAC's are "Multimedia" they may do it btter or have better hardware in them. I haven't done much in the way of research but prob a Dual USB 800Mhz or so would be the PPC side of things or a standard IBM PIII ...

---

### Post by 3rdalbum on 2006-08-14
You want to record and edit audio on Linux? Definately get an x86 PC.

The Macintosh reputation for being good for audio is actually due to the operating system. On the Mac OS, audio "just works" all the time.

Furthermore, many Macs have sound cards which are not supported for input through ALSA. If you do decide to get the Mac (you get more speed per megahertz with G3 over P3), make sure you get one which is fully supported.

Or you could always keep Mac OS on the laptop, and use that for your audio.

---

### Post by stmiller on 2006-08-14
Yes, audio hardware in PPC Linux is not supported/developed as well as x86. It's somewhat frustrating.

Jack and alsa do not work so well on PPC. Just recently they are working better, but not as good as a good old soundblaster card in Linux on x86.

---

### Post by discosammy on 2006-08-14
why couldn't one install a sb live in a ppc?

it's a pci card right? 

there are linux drivers for it right?

isn't it possible?

---

### Post by 3rdalbum on 2006-08-15
I still don't think you could install a PCI card into a Mac without it already having Mac support.

PCs use a startup system called a BIOS. Macs use a system called Open Firmware, which (among other things) registers PCI cards with the computer. If the card doesn't have specific compatibility with Open Firmware, it cannot be made available to the computer.

That's just my understanding of it. Plus, of course, only the tower Macs have spare PCI slots.

---

### Post by discosammy on 2006-08-15
so it preceeds the OS? damn. i was hoping for a shortcut.

---

