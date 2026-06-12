---
title: "Weighing My Booting Options"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-21
I've been going back and forth about what kinda setup I want to use
with Ubuntu and I am still trying to make that decision. What I'd like to
do is have both Windows and Ubuntu but not have it affect my Boot
loader and not be Slow as it would in a Virtual Machine. I'm thinking
Booting from an external USB drive would be the best option but
I'm not sure what kinda performance hit it would take.  Currently
I'm running Ubuntu in Virtual Box and it's not screaming fast but
works pretty well... The down side to this is I can't Write to CD's,
it will only allow reading of Data CD's. One other draw back to
a VM is they don't support 3d so compiz or beryl is out.

Anyone tried Using a USB Drive..... Is it near native speeds?
Thanks guys.... Hopefully I'll choose whats right for me sometime
soon.

---

### Post by steve.horsley on 2007-10-21
It is possible to get Grub to install onto the root / Ubuntu partition instead of installing to the MBR (it's an option dufing install). But then of course you will have to get the Windows bootloader to load the / partition, and I don't know how to do that although I gather it's possible. 

I don't understand what's so precious about your bootloader though. You can't dual boot without making **some** change to it.

---

### Post by daniel_szollosi-nagy on 2007-10-21
I was also faced with this option, as I was too scared of screwing up my partitions while installing Ubuntu.

I found that [Wubi]("http://wubi-installer.org/") does the trick perfectly. As its name indicates, it is a Windows Ubuntu installer. It's an .exe file that you can run from your Windows desktop. It creates a virtual partition for Ubuntu - that is, one huge file (up to 30 GB) that Ubuntu lives inside. Windows just sees this as a big file, but Wubi can boot into it. 

The only significant modification Wubi makes is to your Windows boot.ini, to include an option to boot Ubuntu. If you've upgraded from Win2000 to XP you may have already seen this screen - it's a text mode screen before the Windows logo loads.

As far as Ubuntu is concerned, it's on a large hard disk - it does not care that it's really just a virtual partition on your real Windows hard disk. It's a real Ubuntu without the worries of repartitioning, with full 3D support and everything.

Wubi will download the alternate ISO, so depending on your connection speed it may take a while, but once it's done, the installation is pretty straightforward.

---

### Post by Orbital75 on 2007-10-21
Sounds interesting..... Yeah, I have opened up the Boot.ini file before to look
at it's contents so I see what your saying.... It will add a line below my XP
so during boot it knows there are 2 operating systems and gives you the
option to choose.

Thanks

---

