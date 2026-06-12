---
title: "Move Ubuntu to new hardware"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-01-02
I am absolutely new to Linux. I have installed Ubuntu 7.10 on a P3 800MHz with 312Mb RAM. I like it very much. I have updated it and also configured Samba. It is installed on a 40Gb HDD with 15Gb and 25Gb partition. /home is on the 25Gb partition. I could do all this with help from internet as I had no idea of Linux working. Now I want to move this hard disk to a new and faster machine. I could not find much info on the net. Can anyone give detailed instructions on how to do this. I  hope it is possible as otherwise I will lose lot of time to install Ubuntu and update it again. Please advice.

---

### Post by GuitarRocker2562 on 2008-01-02
ugh, you can just switch the drive, but you would need to reinstall grub, as to how to do that, i don't know

---

### Post by PPAAUULL on 2008-01-02
And you would have to reconfigure some thing like xorg and such but that isn't hard if you know what you are doing. Does anyone know if you would have other problems that would have to be ironed out other then GRUB (I think you can get a cd to install it) and Xorg?

---

### Post by jesrani on 2008-01-02
Grub, Xorg!!!! I said I was absolute newbie and these terms make me a bit scared. I need detailed instructions if possible, please. But I am amazed that I got 2 quick replies. Thanks for this. Please try to help me with more detailed instructions.

---

### Post by GuitarRocker2562 on 2008-01-02
forgot about Xorg, I figured he/she is using the same screen + a better card, so it would just not be optimized, thanks

---

### Post by GuitarRocker2562 on 2008-01-02
haha, i remeber those days,

Xorg - responsibe for all graphics on almost every linux desktop system (if not all)
Grub - the thing that shows up before ubuntu boots with the short countdown.

---

### Post by ~LoKe on 2008-01-03
Bah.  I built a totally new computer, all that was the same was my hard drive.  Just pop it into the new machine and it'll boot up just fine (at least, it should).  Grub should be alright, it should detect the partitions just fine.  See if you can boot it up.  If not, boot up a LiveCD or use another computer to come back here and tell us if you're getting any errors.

---

### Post by GuitarRocker2562 on 2008-01-03
really, never knew that, i will try that one day.

---

### Post by ~LoKe on 2008-01-03
> **GuitarRocker2562 said:**
> really, never knew that, i will try that one day.

No promises.  That's just the experience I had, which is odd since usually everything goes wrong for me (hardware and software. ;)).  But this isn't Windows, and it doesn't really tie into your hardware except your hard drive.

---

### Post by Ardghal on 2008-01-05
So, say, changing the processor, motherboard, RAM and graphics card could leave Ubuntu still working? I'm about to change all that, plus get a SATA2 drive in addition to my IDE.

I was told I will need to reinstall Ubuntu because it won't detect the new hardware like XP does... and when I asked if I could move the SO from the IDE to the SATA, I was also told *Linux doesn't work in SATA*. :(

So, what do you think Ubuntu* can* detect? :confused: I'd be happy if it detected enough stuff as to be able to start; like XP does. From that point, it gets easier to get everything else working.

---

### Post by Ardrias on 2008-01-05
It does work with SATA, seeing as I've got a SATA-only system here at the moment.

What I would do is change all the hardware and clone your old drive to the new one and resize the partitions with something like gparted. You will need to re-install GRUB however, something there's quite a few posts around this forum about. I'd help you find one, but I'm off now. Basically you boot from a live-cd and reinstall GRUB to the new disk you cloned the old one to. 

Or you could do a fresh install and just mount the old disk with your /home on and copy that data to the new one.

---

### Post by Ardghal on 2008-01-05
So, the system *will* detect all the new hardware? A friend told me he could no longer start Ubuntu after he changed his graphics card. As long as the system is able to start, it wouldn't be **so** bad...

Assuming everything will be OK, where could I find that GRUB installer?

---

### Post by jesrani on 2008-01-15
Just to update everyone since I was the one who started the thread. Actually the spare computer I had turned out to be a P2, 800MHz, slower than the one on which I had installed Ubuntu (P3, 1.1GHz).
Before 7.10, I had installed 7.04 on another HDD and just tomo see what happened I put this on the older machine. It just started like usual, no problems. But I dont know if the same thing would happen while shifting to new hardware.

---

