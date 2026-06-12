---
title: "simple Question: How do I boot from CD?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-05-01
I have a dual boot set up, of Ubuntu Dapper Beta and Ubuntu Breezy Badger.

I want to keep the Dapper but I want to install SUSE as my second boot.

I put the CD in and restart but it doesn't boot, do I need to enter something at the GNU Grub menu?
:-k

---

### Post by Titus A Duxass on 2006-05-01
Are your BIOS settungs correct, look for boot devices and make sure CD is the first.

---

### Post by RAV TUX on 2006-05-01
[QUOTE=Titus A Duxass]Are your BIOS settungs correct, look for boot devices and make sure CD is the first.[/QUOTE]

how do I even access the BIOS menu when Ubuntu is my only OS?

I know how to access the BIOS on windows but not Ubuntu.
:-k

---

### Post by Titus A Duxass on 2006-05-01
During the boot process right at the very beginning you are normally given an instruction to press Delete or F2 (or another key) to enter the BIOS setup.

---

### Post by RAV TUX on 2006-05-01
[QUOTE=Titus A Duxass]During the boot process right at the very beginning you are normally given an instruction to press Delete or F2 (or another key) to enter the BIOS setup.[/QUOTE]

nope it just goes to GNU Grub.

do you know of a command line I can enter? I see the c prompt for command line.
:-k

(very old computer 1998 at least, even upon the first install of the Hedgehog, last year I never had to go into the BIOS menu. Now on my new computer I see exactly what your talking about but that is a different story)

---

### Post by Sef on 2006-05-01
Usually to get into the BIOS, you have to push F2, esc, or delete.   As soon the the computer starts to boot up, keep pressing one key.  If it doesn't go into the BIOS, then start over and keep pressing another key.

Note: Occassionally it is another key, but those three are the most common.

---

### Post by RAV TUX on 2006-05-01
[QUOTE=Sef]Usually to get into the BIOS, you have to push F2, esc, or delete.   As soon the the computer starts to boot up, keep pressing one key.  If it doesn't go into the BIOS, then start over and keep pressing another key.

Note: Occassionally it is another key, but those three are the most common.[/QUOTE]

OK I'll try again, but like I said I have never had to go into the BIOS even when I installed Dapper from a CD I burned a few days ago.

but I will try F2 and let you know how it goes.

I have tried a live CD of Scientific Linux and now a install of SUSE and neither automatically boot like all three Ubuntu CD's have; Dapper, Breezy, & Hoary.
:-k

---

### Post by Sef on 2006-05-01
When the boot starts, it usually tells you what key to push to get into the BIOS.

---

### Post by Titus A Duxass on 2006-05-01
Are you sure that your SuSE CD is okay, does the boot process tell that it is looking for a bootable CD?

---

### Post by manicka on 2006-05-01
[QUOTE=yozef]OK I'll try again, but like I said I have never had to go into the BIOS even when I installed Dapper from a CD I burned a few days ago.
[/QUOTE]

Sounds like you have a  faulty install disc. Burn a new one at a lower speed and see if that makes a difference.

How did you create your SuSe cd's? Were they from iso images?

---

### Post by RAV TUX on 2006-05-03
[QUOTE=manicka]Sounds like you have a  faulty install disc. Burn a new one at a lower speed and see if that makes a difference.

How did you create your SuSe cd's? Were they from iso images?[/QUOTE]

CD's checked out as fine on the CD check.

I loaded PCBSD as a dual boot but then I decided that I am completely happy with Ubuntu Dapper and will only run Ubuntu (on this computer).

---

