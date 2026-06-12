---
title: "cdrom problem"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Oblid on 2008-01-11
**Im no speking english (Uruguay-Spanish).**

No install

CD-Rom Primary Slave = OK :-) install perfect

CD-Rom Secondary Master = OK :-( no install

Same problem in Ubuntu - Suse

How install in CD-Rom Secondary Master?

**En español (in Spanish)**

Cuando intento instalar Ubuntu (o SuSe y otras distros) tengo que desarmar el PC y conectar la lectora de CD en esclavo del HD sino no se instala. Me da un error como que la unidad es lenta (slow dma 33 soft reset). Con Mandriva 2007 no tengo problema

---

### Post by nikoPSK on 2008-01-11
So basically your master cd drive doesn't work? They should right off the bat unless maybe a problem with your drive....

---

### Post by Oblid on 2008-01-12
**Is the same drive**

CD-Rom Primary Slave = OK :-) install perfect

CD-Rom Secondary Master = Bad :-( no install **(hang 21%- libc6-udeb)**

Same problem in Ubuntu - Suse

How install in CD-Rom Secondary Master?

---

### Post by LinuxGuy1234 on 2008-01-12
> **Oblid said:**
> **Is the same drive**

CD-Rom Primary Slave = OK :-) install perfect

CD-Rom Secondary Master = Bad :-( no install **(hang 21%- libc6-udeb)**

Same problem in Ubuntu - Suse

How install in CD-Rom Secondary Master?

Some CD-ROM drives don't go well with Ubuntu CDs. What is your CD-ROM drive called? (the model, make, type and all of that stuff)
Example: hdc: LITE-ON DVD C LH52C1P, ATAPI CD/DVD-ROM drive
Example 2: hdd: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
Find this using dmesg | less.
When you get to something like (after scrolling down):
[17179573.828000] Probing IDE interface ide0...
[17179574.120000] hda: ST340015A, ATA DISK drive <- Hard drive
[17179574.792000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.792000] Probing IDE interface ide1...
[17179575.192000] hdc: LITE-ON DVD C LH52C1P, ATAPI CD/DVD-ROM drive <- This is what you look for
[17179575.976000] hdd: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive <- If you have a second CD/DVD-ROM drive
[17179576.032000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.048000] hda: max request size: 128KiB
[17179576.068000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.068000] hda: cache flushes supported
[17179576.068000]  hda: hda1 hda2
[17179576.144000] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33) <- :popcorn: Also this is what you look for
[17179576.144000] Uniform CD-ROM driver Revision: 3.20
[17179576.148000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33) <- :popcorn: Also this is what you look for (if you have a second CD/DVD-ROM drive)

---

### Post by Oblid on 2008-01-13
Yes, is the same problem. But no is the cdrom drive. I plug the same drive in slave of sda (IDE 0 in my motherboards) and work. But master of IDE 1 and not.

---

### Post by Moop on 2008-01-13
Have you checked the jumper settings on the back of the cd player? It could be set up as a slave. Set it to CS (cable select) and it should work either way. With older hardware you may need to use the master/slave settings.

---

### Post by rkd on 2008-01-14
When you moved your CD-ROM drive to the secondary IDE port, I think you used a different ribbon cable to connect it to the motherboard. Is that correct?

Maybe the ribbon cable is bad. Or maybe the secondary IDE port is bad.

One test you could do: Use another ribbon cable to connect the CD-ROM to the secondary IDE port.

Another test you could do: Connect the CD-ROM as primary slave again. Make sure it still works. Then unplug the ribbon cable from the primary IDE port and plug it into the secondary IDE port. I am assuming that the hard disk is the master on the primary IDE. Moving the cable will move both the hard disk and the CD-ROM to the secondary IDE. But you will be using a cable that you know is good. Now see whether the CD-ROM works. If it does not work, then there is something wrong with the secondary IDE port. If it does work, then maybe the other ribbon cable is bad. Or maybe something else is wrong.

The suggestion that Moop made about checking the jumpers is good, but maybe you already changed the jumpers correctly.

Do some of these things to get more information, tell us what happened, and we will try to help you find the problem.

---

### Post by Oblid on 2008-01-29
My cdrom drive is OK, my IDE ports is OK, my ribbon cable is OK, my cd of Ubuntu 7.10 (alternative and live) is OK .


News of my error: Install hangs when retrieving libc6-udeb

---------------------------------------------------------
exeption emask 0x0 + words + words + number

ata2: port is slow to respond, please be patient
ata2: device is not ready (errno=16) forcing hardrest
ata2: soft reseting port
ata2.00 configure for UDMA/33
EH complet
----------------------------------------------------------

2 o 3 times

After more errors

With Ubuntu 5.10 no problem.

Is possible: new libata driver problem (?). I read in Mandriva docs.
with hdc no problem
with sdc problem

Mandriva 2007.1 ONE (Live CD) installation is OK.
Ubuntu 7.10 and 7.04 (the best linux dist. alternative option is the best for old pc), OpenSuSe 10.3, Fedora 8 = Problem

SORRY my BAD ENGLISH

---

### Post by rkd on 2008-01-29
Your English is OK -- I think we can understand you.

I'm sorry I misunderstood the problem. I guess I did not read your first post carefully. I thought the install fails when the CD drive is on the secondary IDE, but now I see it fails when the CD drive is on the primary IDE.

I will guess that the hard drive is also on the primary IDE. Is that correct? If yes, then there are two factors different between the case that succeeds and the case that fails: (1) CD drive is master when install succeeds but slave when install fails. (2) I/O is separated when install succeeds but all on one IDE channel when install fails.

So maybe the problem is that the CD drive does not work correctly when it is the slave. Or maybe something does not work correctly when the CD drive and hard drive are on the same IDE. Some pairs of IDE devices just do not work together on the same IDE channel.

I think one test that is worth doing: Make the CD drive be primary master and make the hard disk be primary slave. If the install fails, then the problem is related to all the I/O on the same IDE.

If that install works, then make the hard drive be primary master and make the CD drive be the secondary slave. If that install fails, then that CD drive does not work as the slave. I do not know why it would not work as the slave.

If both of these suggested tests result in successful install, then I do not know what the problem could be.  Well, one more idea: maybe the IDE channel is not selected the correct I/O mode for the CD drive. If you know what the I/O mode for the CD drive should be, check the BIOS setup to see whether you can force the IDE to the correct I/O mode.

---

### Post by Oblid on 2008-02-02
Finally, the problem is my cdrw compatibility, y change for 32x old drive (compaq) and work, I will in the future my cdrw work perfect.

---

