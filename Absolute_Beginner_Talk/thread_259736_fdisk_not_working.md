---
title: "fdisk not working"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-17
I am trying to install ubuntu server onto an old dell I have but each time I use fdisk(win98boot disc) it says that                                       there are no fixed discs present??? I know that the disk is  plugged in and     
the IDE cable is also plugged in too???

---

### Post by xpod on 2006-09-17
IS your bios set to be booting from the floppy before it looks elsewhere?

---

### Post by charles.g.moore on 2006-09-17
Yeah because the win 98 boot disk boots up normally it just says that there are no fixed discs present when I try to fdisk it.  Do you think that the absence of a jumper on the HDD could be the problem???

---

### Post by voodoonirvana on 2006-09-17
Make sure you have your boot device priorities set right.

---

### Post by charles.g.moore on 2006-09-17
Yeah but for some reason the bios isnt even seeing the HDD I have installed in the box???

---

### Post by xpod on 2006-09-17
I think that could be a possibility...But why would you have it set as anything other than what it should be set as??

Im no expert mate but that was something i think i had to have right before i could get to first base...I messed about with "third" drives when i had Xp and Ubu on separate drives and somehow messed the two of them up with my messing about trying to get jumpers correct(no guide on the hd!).

I think thats what it must ahve been.But i did`nt need to do no partitioning just prior to it so dont know for sure.
I would reckon you should have them all set correctly before proceeding rather than find out later ](*,)

EDIT:..oh well ,theres some proper advice for you now:biggrin: 
Goodnight and good luck

---

### Post by crokett on 2006-09-17
What kind of disk? IDE or SCSI?  Any other disks or a CDR drive on that cable?  

If BIOS does not see the drive, don't bother booting all the way to 98.  

What size is the drive? Does the dell support that large a drive? 

Check cables, including power cable to drive.

Check your BIOS.  If BIOS autodetect for drives is disabled and you change drives, you need to manually rescan to find the new drive.

If IDE, and it is a single drive jumper it to master.  If another drive on the cable, this should be set to master and other drive to slave. 

If SCSI check power and cable connections and verify no SCSI ID conflicts with another device on the cable (this includes the SCSI controller)

---

### Post by bodhi.zazen on 2006-09-17
Why not bood the live CD and use fdisk from Linux.

---

### Post by Kilz on 2006-09-17
> **bodhi.zazen said:**
> Why not bood the live CD and use fdisk from Linux.

I think he is using the boot disk to boot the old dell. Perhaps the old dell is so old the bois doesnt have the ability to boot from cd.

---

### Post by bodhi.zazen on 2006-09-17
> **charles.g.moore said:**
> ... each time I use fdisk(win98boot disc)...

How are you running fdisk, win98 boot disk or Ubuntu install/live cd ?

---

### Post by charles.g.moore on 2006-09-17
I dunno what happened but I got it working...
I was using the win98 boot disk to use the fdisk utility...
For some reason i could not get the PC to see the HDD unless it was on the same IDE cable as the CD-ROM
I took some juggling with the jumpers to finally come to the right configuration but as it looks now the HDD is the master on the Primary
and the slave is the CD-ROM
Like I said before I just want it to use as a web server that I can break...

Thanks all

And Bodhi, you're help with my xorg really came in handy, I finally got my dual monitor setup working perfectly and I love it, maybe if you have time Ill hit you up with some questions I have in another thread say in like a half hour or so...

---

### Post by bodhi.zazen on 2006-09-17
> **charles.g.moore said:**
> And Bodhi, you're help with my xorg really came in handy, I finally got my dual monitor setup working perfectly and I love it, maybe if you have time Ill hit you up with some questions I have in another thread say in like a half hour or so...

So it was a problem with the hardware? I assume you found an inexpensive adapter? Please post your solution in the old thread so others may learn.

I am glad I could help. Just do not make your next question too hard. The last one made my brain hurt. :lol:

---

