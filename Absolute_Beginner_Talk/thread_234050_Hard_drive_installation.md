---
title: "Hard drive installation"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by mapleshade on 2006-08-10
I put a new 500GB MAXTOR SATA hard drive in my computer running Dapper LAMP server.  It doesn't show up with fdisk, in the Gnome GUI, or with Gparted (including the Gparted live CD).  It does come up in the BIOS at boot.  How do I format and mount a drive?  I'd like to use the XFS file system.

---

### Post by em3raldxiii on 2006-08-11
I'm not precisely sure I know how to answer your question as I am not really a guru, but I'll ask a couple of questions that may help.

1.  Some motherboards require that you put certain drives on certain SATA channels.  One such was an Asus board I set up that required the boot drive be on channel 3 and the other drives on 2 & 4, and leave 1 for last (I think that's how it was).  It *might* be that if you changed which SATA channel it's on it might help.

2.  Is the power connector fully engaged and/or does it have a problem?  I have heard of one case where the drive was indicated in POST at boot time, but not in Linux, and it turns out the SATA cable was in, but the power was not.

3.  Does your BIOS know how to handle drives of that size?  Its a long shot, and others may be able to confirm or deny this concern, but the drive might be too large for your motherboard (in which case you may be able to flash the bios).

So yeah ... just a few questions that *may* help.  Either way, I bumped this thread up to the top again ;)

---

### Post by mapleshade on 2006-08-11
> **em3raldxiii said:**
> I'm not precisely sure I know how to answer your question as I am not really a guru, but I'll ask a couple of questions that may help.

1.  Some motherboards require that you put certain drives on certain SATA channels.  One such was an Asus board I set up that required the boot drive be on channel 3 and the other drives on 2 & 4, and leave 1 for last (I think that's how it was).  It *might* be that if you changed which SATA channel it's on it might help.

2.  Is the power connector fully engaged and/or does it have a problem?  I have heard of one case where the drive was indicated in POST at boot time, but not in Linux, and it turns out the SATA cable was in, but the power was not.

3.  Does your BIOS know how to handle drives of that size?  Its a long shot, and others may be able to confirm or deny this concern, but the drive might be too large for your motherboard (in which case you may be able to flash the bios).

So yeah ... just a few questions that *may* help.  Either way, I bumped this thread up to the top again ;)


1. I do have an Asus board (A7N8X).  The boot drive is PATA.  I only have 2 SATA channels, there is a 320GB drive on one and the 500GB on the other.  The 320 is shown with fdisk -l, Gparted, etc.  The 500 is not.

2. Interesting, I'll check the power cable.

3. During POST, it shows up as a Maxtor drive, 479000KB.  Which would lead me to believe that it is properly recognized by the BIOS.

Thanks for the bump.  I thought I was not doing something, but it may be an issue with Ubuntu?

---

### Post by mapleshade on 2006-08-11
OK, so I unplugged the cable from my 320 SATA and plugged the 500 in to the 1st SATA channel.  I fired up Gparted and made an XFS partition.  I shut down the computer and plugged the 320 back into channel 1 and the 500 into channel 2.  Both show fine at POST, but I can still only see the 320 in Ubuntu.  Apparantly there's a problem with the second channel on my mobo's SATA controller and Ubuntu.  Any ideas, short of getting a PCI SATA controller?

---

### Post by em3raldxiii on 2006-08-11
Well, unfortunately I have no idea because I rarely delve into that sort of matter.  However, I am absolutely CERTAIN that someone around here will have the answer for you - it's just a matter of connecting with the right person.  That or use the IRC channel (#ubuntu) but I can't remember which server ... I'm by no means an IRC buff either LOL.  I do know that you can get INSTANT help there though.

---

