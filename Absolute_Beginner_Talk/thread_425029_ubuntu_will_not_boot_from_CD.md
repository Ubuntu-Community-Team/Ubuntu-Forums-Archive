---
title: "ubuntu will not boot from CD"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by wizardofaus on 2007-04-27
Or more precisely:

Ubuntu will boot from the CD as long as I do not have a hard drive in the machine.

The computer is an old Dell - plenty of power for running ubuntu - with windows 2000 pro installed. There are serious issues with the win2000 (it's an ex network machine and cant find components) and as this is a spare machine I thought I would experiment with linux.

The trouble is that when there is a hard drive in the machine the PC won't boot. I have tried hotplugging a hard drive after the comp starts from CD but the disk doesnt load.

Is there a trick to this? I have searched the database, but eitehr I havent hit on the right set of words, or I am the only person in the world with this problem............

---

### Post by Sef on 2007-04-27
Have you gone into the BIOS and set the CD drive to boot before the hard drive?  To get into the BIOS, you need to push one of these buttons (usually): F2, esc, delete or other.   Upon boot up, your computer will tell you what button to push to go into the BIOS.

---

### Post by wizardofaus on 2007-04-27
I have tried that too......... nothing will bring up the bios (!?)

What I am trying, however, is reformatting the current hard drive in another machine, and then I will try to get the machine to boot from CD with the newly empty hard drive installed

more soon.........

---

### Post by Cypher on 2007-04-27
**Sef** got it spot on, the BIOS is set to boot the HD first and then go to the removable devices. If you format the HD, then you will get the CD to load, but if you ever wanted to run the LiveCD later on, you'll have to re-do this step.

It might be worthwhile figuring out how to get into the BIOS for your machine. Immediately after power-up, start mashing all of the F1-F12 keys, one of them has to do it..

---

### Post by paparucino on 2007-04-27
> **Cypher said:**
> 
It might be worthwhile figuring out how to get into the BIOS for your machine. Immediately after power-up, start mashing all of the F1-F12 keys, one of them has to do it..

Try with "delete", too. On my machine BIOS isa called via Cancel/delete

---

