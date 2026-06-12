---
title: "How to install Ubuntu with a serial ATA adapter"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Pierangelo on 2005-12-22
Firt of all I woud like to say hello to the Community Chat Forum.:KS

I'm trying to install Ubuntu on a P3 500 Mhz with HighPoint Technologies RocketRAID 1520 host adapter. The hard disk is WD740 Raptor. When the installation comes to Partman I can't make any opperations, there is no hard disk recognized. Help!

---

### Post by Pierangelo on 2005-12-22
[QUOTE=Pierangelo]Firt of all I woud like to say hello to the Community Chat Forum.:KS

I'm trying to install Ubuntu on a P3 500 Mhz with HighPoint Technologies RocketRAID 1520 host adapter. The hard disk is WD740 Raptor. When the installation comes to Partman I can't make any opperations, there is no hard disk recognized. Help![/QUOTE]
............................................................................................................

---

### Post by Rinzwind on 2005-12-22
Hmm. I don't see anyone that got it working...

From the highpoint site:

[http://www.highpoint-tech.com/USA/faq_rr1520.htm](http://www.highpoint-tech.com/USA/faq_rr1520.htm)
> **Can I boot the system from a drive attached to the RocketRAID 1520 card?**
Yes. The RR1520 card's has it's own independent BIOS, which allows operating systems to be installed to, and booted from, drives or arrays attached to it's IDE channels. The card supports most Windows operating systems (Win2k, XP, NT, Win98/ME), several versions of Linux (Red Hat, SuSE, Caldera, Turbo), and FreeBSD.

- Maybe you need to install a driver 1st. 
- Have the discs been formatted before? If not you need to do that 1st from within the software for the card itself (you should be able to go into that after your system boots (there should be a "press F2 to enter")).

I aint much help tho :( 

Oh and do wait a few minutes longer ;) Alot of people are sleeping or working at the moment.

---

### Post by Pierangelo on 2005-12-22
Hello Rinzwind,
It's nice to answer me. You are my first contact on these forum!!!!!
There is no need to install a driver for Debian/Ubuntu.
I guess the disc is formatted, I have allready installed XP before.
I'm going to have a look at the Highpoint site...

---

### Post by Rinzwind on 2005-12-22
[QUOTE=Pierangelo]Hello Rinzwind,
It's nice to answer me. You are my first contact on these forum!!!!!
There is no need to install a driver for Debian/Ubuntu.
I guess the disc is formatted, I have allready installed XP before.
I'm going to have a look at the Highpoint site...[/QUOTE]

Ok if it's allready had an OS I think it's weird it didn't see your drives.
But it should be a driver issue: those cards require a driver to be started 1st before you can see the drives. Stupid I know :(

---

