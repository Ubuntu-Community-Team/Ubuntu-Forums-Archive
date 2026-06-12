---
title: "My last Try to install it , can anyone help me?"
date: 2007-04-20
forum: Apple PPC Users
---

### Post by brunometal on 2007-04-20
well,

2 weeks passed , I 'm trying to install Ubuntu on my G3

too much errors.. 

I can run MacOSx very fine, I can Run GentooLinux Very fine

But.. I really want Ubuntu in there !

The newest release of 7.04 Lice-Cd works very fine , I can boot from live cd and I can do everything with live CD, but I can't install, no instalation success with Live-cd ( the aec62xx issue), and no success with alternate cd (/target copying issue)..

if there are no ideas to install Ubuntu on my Mac .. I will leave it.. and i will run macOsX ( but I dont like it)

My Idea:

Can I make a copy of the live cd ? and write the live cd image to Hd, then will be able to start and change things there?

can I do it with dd?  dd if=/dev/ramdisk of=/dev/hda ???????? it works??

anyone have an idea ?


My Bug
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107740](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107740)

---

### Post by stmiller on 2007-04-21
What is the target/copying issue? Explain in more detail. Sounds like either a hard drive problem or a bad cd image.

---

### Post by wusl.au on 2007-04-22
I'm having the same problem - Installation hangs at 91% 'Loading module aec62xx'.

I've verified the CDROM and it appears OK.  Looking on the 'net I can see suggestions to reduce RAM to 512MB - done that.

I've tried killing the process 'log-output -t hw-detect modprobe -v aec62xx' and the detection just steps on to another driver, which also hangs.

The actual modprobe processes will not die, even with kill -9.

I'm trying to install on a G4 Power Mac, 400MHz ( Sawtooth ).

Wusl

---

### Post by Heybes on 2007-04-23
Yip, I am also hanging 91%. When I browsed my VAR/LOG/SYSLOG it seems that the error occured just before "aec62xx" install was attempted. Error: no floppy controller.

Error:

floppy0: no floppy controller found
FATAL: Error insering floppy (/lib/modules/2.6.20-15-generic/kernel/drivers/block/floppy.ko); No such device

Then it goes on to install what I "thought" to be the problem, the "aec62xx" drivers, but there are no errors on installaion of "aec62xx" in the VAR/LOG/SYSLOG.

Can anyone please explain to me how to do an CD installaion and tell the installer to ignore the floppy installation!!!

Windows has made me a softy!!!  :lolflag: 

GUI is so nice, that is if it works!!!

---

### Post by wusl.au on 2007-04-24
Well, sick of wasting my time on a apparently lost cause, I decided to try loading 7.04 on my Power Mac instead.

Guess what?  Same damn error.  It still stops at 91%, apparently trying to load aec62xx.  I wondered whether maybe I had a dodgy Mac, but hey, it runs OS-X just fine.

How many people *really* have got a late version on PPC Ubuntu to work on their 400Mhz G4 Power Mac?

OpenSUSE is looking like my best port of call now.  I wonder if anyone's got that working on Macs?

Anyone got ideas?

---

