---
title: "Old un-identified sound card."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by dragonflyseven on 2006-08-08
I know this is a long shot, but none of the other threads have been able to help, so I thought I would ask. I have installed Xubuntu on an old HP Pavilion 6730 (Designed for Windows 98), and I cannot get the sound to work. My main problem is that I don't know the make or model of the sound card, so I was wonderinf if anybody knew of a program that automaticlly searched for and setup sound cards. Thanks in advance.

---

### Post by carlosqueso on 2006-08-08
try using lspci to see what ubuntu thinks it is.

---

### Post by davebgimp on 2006-08-08
If it is recognized, but not being used, check your BIOS and try disabling inboard sound. I've found that with sound cards, Ubuntu will sometimes use the inboard sound instead. Disabling it in the BIOS will have Ubuntu use the next available thing...your card.

---

### Post by bscbrit on 2006-08-08
Are you the brave sort of person that opens computers to look inside?  Do you feel confident enough to remove the sound card?  If you do, you will probably find a maker's number, FCC identifier or some such on the board somewhere.  A quick Google for the numbers usually comes up trumps for me.

The sort of program you a describing is exactly what takes place during Ubuntu installation.  It test for various cards, and if it finds them it installs the appropriate software driver.  If it didn't work during the install I can't imagine another program that will do what you want.

---

### Post by tommyp on 2006-08-08
You should look up ALSA project to see if any drivers exist, plus some good directions on how to install

I've got an HP too, and it came with a combination sound card/modem - the Rockwell Chameleon.  I could get the 56K modem to work (yipee :neutral: ) but not the sound card.  I eventually gave up and bought a $7 sound card.  Worked great on the first boot!

Good luck!

---

