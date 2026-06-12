---
title: "Bare metal backup for G3/G4 (PowerPC) Mac systems?"
date: 2018-12-25
forum: Apple Hardware Users
---

### Post by jharris1993 on 2018-12-25
Greetings!

**_Assume_:**
[LIST=1]
[*]The base system is a Mac based system that might have had one or more Mac O/S's installed at some point in time. 
[*]It is relatively recent. (New World Mac) 
[*]It runs the PowerPC architecture, not Intel. 
[*]It is fully functional.  (*i.e.* No hardware issues) 
[*]It has some version of Linux installed and running - though maybe not with a GUI. 
[*]It has a combination of Apple and Linux partitions on it's hard drive. 
[*]It is desirable or necessary, (for whatever reason), to do a ***total, bare-metal backup***, where a "total, bare-metal backup" is defined as the ability to take a backup image and restore it to a ***completely blank hard drive*** - or a hard drive that has ***never been used in a Mac-based system***.
(Perhaps for software QA, troubleshooting, fixing PPC software bugs, etc., where the system needs to be restored to a known state periodically.) 
[/LIST]

**_Also assume_:**
[LIST=1]
[*]It is ***not reasonably possible*** to physically remove the hard drive from the system and migrate it to another computer.
This is because some systems do not have user-accessible hard drives, but require total disassembly to remove or replace it. 
[*]It is ***not possible*** to boot or back-up using a firewire connection.
This is because external firewire based storage is, essentially, nonexistent at this point in time.  (. . . and what ***does*** exist costs more than the cost of replacing the system with some beast Alienware monster. #-o:roll:) 
[/LIST]

**_Case 1_:**
The system is an older New World system that ***_cannot_ boot from USB***,  (iBook G3, etc.), but has a working and bootable optical media device installed. (CD/DVD)

**_Case 2_:**
The system is a New World PPC based system that ***can boot from USB***.  (Later PowerPC based Macs)


**_Question_:**
With respect to both cases, is there some way to perform a total, bare-metal backup of a Mac based system so that a total bare-metal restore can be done at a later point in time?

The object of all this, as mentioned before, is to have the ability to absolutely and totally restore a system backup, to bare-metal hardware, that results in an exact working and bootable copy of the system as it was at the time of the backup.

Thanks for any help or advice you can give.

Jim "JR"

---

### Post by gsahli on 2018-12-25
How about "dd" (disk duplicator)?
[https://www.geeksforgeeks.org/dd-command-linux/](https://www.geeksforgeeks.org/dd-command-linux/)

---

### Post by jharris1993 on 2018-12-25
> **gsahli said:**
> How about "dd" (disk duplicator)?
[https://www.geeksforgeeks.org/dd-command-linux/](https://www.geeksforgeeks.org/dd-command-linux/)



Two questions:
1.  "dd"  produces a 1:1 copy.  I know I can g-Zip it, but am not sure how accurate the un-zip will be.
2.  A Mac based disk doesn't use a "normal" DOS-type MBR as far as I know.  the Mac disklabel is a whole 'nother beast.  Normally, when I use "dd" for something like that, I also use a seperate dd command to copy just the first 512 bytes.  I don't know if that will work on a Mac based disk.

Thanks!

Jim "JR"

---

### Post by gsahli on 2018-12-26
I guess I don't understand what you need. dd can duplicate the entire drive including partitions and boot sector, etc.

---

