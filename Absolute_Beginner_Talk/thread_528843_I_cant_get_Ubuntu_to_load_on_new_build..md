---
title: "I cant get Ubuntu to load on new build."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by asmo on 2007-08-18
Ubuntu doesn't work and won't even boot I've tried 7.04 and the 7.10. Gentoo, Debian, Fedora, the list goes on you name it and it wont boot on my computer. It has to be something to do with my sata dvd drive because I managed to boot ubuntu livecd once when I was using an IDE drive. I wont post the exact error messages I get because I'd be typing well into the night but heres an over view from ubuntus error messages:

ata1.00: revalidation failed (error=-5)
[(random number)] Buffer I/O on device sda, logical block 0
[(random number)] Buffer I/O on device sda, logical block 1
[(random number)] Buffer I/O on device sda, logical block 2
[(random number)] Buffer I/O on device sda, logical block 3
[(random number)] Buffer I/O on device sda, logical block 0
[(random number)] Buffer I/O on device Sr0, logical block 0
[(random number)] Buffer I/O on device Sr0, logical block 1
[(random number)] Buffer I/O on device Sr0, logical block 2
[(random number)] Buffer I/O on device Sr0, logical block 3
[(random number)] Buffer I/O on device Sr0, logical block 0
[(random number)] Buffer I/O on device fd0, logical block 0
[(random number)] Buffer I/O on device fd0, logical block 1
[(random number)] Buffer I/O on device fd0, logical block 2
[(random number)] Buffer I/O on device fd0, logical block 3
[(random number)] Buffer I/O on device fd0, logical block 0

Then after repeating a little while longer I get:

atta2.00: exception Emask 0x0 SAct 0x0 action 0x2 frozen
ata2.00: cmd a0/00:00:00:00:20/00:00:00:00/a0 tag 0 cab 0x0 data 0

It then repeats itself again until at the end I get this:

/bin/sh: cant access tty: job control turned off
(initramfs)

I've tried the alt cd and it couldn't find the cd/dvd drive even though it had just booted from it, and in gentoos livecd it couldn't boot because it couldn't find the bootable drive. When I try to check the integrity of the cd I get error messages. Could it be the sata dvd drive or is my computer the one old bills been dreaming of.

Here my computer spec:

Asus V3-M2A690G AM2 Mobo
AMD Athlon 64 X2 4600+ CPU
Crucial 2GB kit RAM
ATI integrated graphics

Any help would be apreciated as I don't know what to do thanks.

---

### Post by asmo on 2007-08-19
Don't worry guys I've found out why, Ubuntu can't handle sata dvd drives, never mind. Cheers anyway.

---

