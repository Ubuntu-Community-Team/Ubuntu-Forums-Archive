---
title: "Ubuntu under virtualization"
date: 2008-03-25
forum: Apple Intel Users
---

### Post by gdsegel on 2008-03-25
Hi All,

Tried looking for a good answer, but was unable to locate. Hope you can help this newbie.

I'm looking to install Ubuntu on my MacBook (black) 2.2 GHz. Instead of running live from the DVD or under BootCamp, I would like to either run under VMWare Fusion or Parallels.

Any positives or negatives to this or any feelings regarding either program?

Thanks for your help!

Gregg

---

### Post by keisunesu on 2008-03-26
You might want to try the free [VirtualBox]("http://www.virtualbox.org/") before shelling out $80 for VMWare or Parallels, just to see whether or not virtualization is enough to meet your needs.

---

### Post by cyberdork33 on 2008-03-26
no 3D acceleration in a VM. This means no compiz / beryl special stuff.

---

### Post by Playercoca on 2008-03-26
Trough Parallels, you can have 3D effects, I think, read the Parallels website :-)

---

### Post by cyberdork33 on 2008-03-26
> **Playercoca said:**
> Trough Parallels, you can have 3D effects, I think, read the Parallels website :-)
It can emulate DirectX yes, but not 3D acceleration with Linux no.

---

### Post by mrsteveman1 on 2008-03-27
VMware fusion is fast, parallels is more integrated (but thats with windows not sure about ubuntu).

---

### Post by redfox on 2008-03-27
I have had a good experience running the current and previous Ubuntus in Fusion.  One the VMWare tools are installed, things work quite nicely.

I haven't tried Parallels, though.  I don't know if they have utilities that can be compiled for linux like VMWare has.

---

### Post by hackersmovie on 2008-03-28
I tried Ubuntu in both Parallels and VMware Fusion, neither worked perfectly. Parallels for me was just really buggy, Fusion wouldn't correctly recognize the DVD drive and kept freaking out my blue tooth keyboard, the solution for me, Boot Camp. If your running Leopard, you can repartition the drive with Boot Camp Utility without disrupting your OS X install, I would also highly recommend rEFIt in lieu of holding the option/alt key. . . My .02. . . 

This was done on a 17" iMac 1.83Ghz CoreDuo, 2GB RAM. . . .

---

### Post by ceratophyllum on 2008-03-28
Q, VMware, VirtualBox, and Fusion have all been slow and buggy in different ways. VMware and Qemu have been kicking around for 5+ years and they never work right.  I guess this is no surprise, considering how much computers have changed in 5 years. The free ones are kind of fun to play with for a day or two, but if VMware and Fusion expect me to buy their software, it had better work perfectly.  I think all these programs will go the way of Ardi's Executor: years into developing a m68k emulator, Apple switches to PPC making Ardi's (still unfinished) product irrelevant. 

Anyway, all virtual machines make my core 2 duo macbook's fan run a lot. Silent computing is a big thing for me, so I can't stand virtual machines. (I'll put up with the fan noise to play world of warcraft, but that's about it.)  Getting files in and out of the virtual machine is always dodgy and you can forget about 3D games working properly.

Just dual boot.  (Unless you enjoy testing broken VMs.)
Resizing my OS X partition with bootcamp was a dream compared to how horrible it was in the days before repartitioning tools matured.  It's a little hassle at first, but sooo much nicer than wrangling with all that perpetually broken VMcrap.

---

