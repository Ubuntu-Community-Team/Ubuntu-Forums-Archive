---
title: "Can't boot from CD"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by kryos on 2007-02-19
Completly wiped HDD w/DBAN, Can boot PCLOS cd but not 6.06 cd.  Can boot both from any other machine tried.  Anything obvious/overlooked/?

---

### Post by Brendantb on 2007-02-19
Hi, 

To start the ball rolling, could you post the specs of the machine you are trying to install on, with details about the cdrom/dvdrom especially.

At what point in the install does the failure take place?

---

### Post by kryos on 2007-02-19
It's is an OLD AMD K62-350/256MB RAM/6.4GB HDD/IDE-ATAPI 40X CD-ROM
Not sure of the make.

---

### Post by deadgobby on 2007-02-19
Often when installing Ubuntu i386 on an AMD64 board you will have to hit F6 and enter the following paramaters

irqpoll pci=noacpi noapic nolapic acpi=off

to get The Ubuntu i386 Alternate or LiveCD to Boot correctly.

---

### Post by kryos on 2007-02-19
OLD AMD K62-350!  Am I feeling old?  Not a 64.  Additionally, the only CD that it will boot is PCLOS. No DSL, Puppy, Mint, Knoppix, System Rescue.  About ready to install a spare CD drive.

---

