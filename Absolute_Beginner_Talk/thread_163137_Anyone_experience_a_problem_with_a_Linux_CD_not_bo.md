---
title: "Anyone experience a problem with a Linux CD not booting on a computer?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by mistergq on 2006-04-20
I have Ubuntu installed on my laptop.  I also have a desktop computer, P4 2.2, that I use it as a Snapstream Beyond TV server (which keeps me on Windows platform on that computer).  I have thought about switching to Myth TV, but after playing around with it and talking to a good friend of mine who has used it for well over 2 years, I decided to stick with BTV...its a quality program, it works for me and my wife knows how to use it!  Anyways, I began having disk errors and in anticipation of a HD failure, I replaced the drive.  (BTW: it is amazing that once the Wife loves technology, she is okay with replacing failing parts, but wanting to buy a new laptop, that can't happen!) The new drive is a 200 GB drive.  

The BTV computer is an HP computer (last HP I will ever buy).  Despite repeated requests during warranty, HP never sent me recovery disk.  A 5 GB partition on the failing hd has the recovery for Windows (among other crap).  I need to get that 5 GB partition over to the new hard drive so I can do a fresh format and rebuild the drive for BTV (in case anything got corrupted during the problems).  A poster on Snapstream recommended HDClone which I believe is built on linux operating system to copy one partition to another.  I made a boot cd, tried to boot with it on the HP, no luck.  However, I could boot with it on other computers.  I saw that HDClone had a floppy disk option which worked.  

The old hard drive was 80 GB, and HDClone made two partitions, one for the 5 GB and a 195 GB.  I then did the recovery program.  After the recovery was completed and I got Windows updated (damn, did that take forever), I wanted to reduce the 195 GB partition.  I put my Ubuntu November 2005 distro disk into the CD drive to complete that task and guess what, it would not boot either.

Here is my question, did HP do something to the original hd partitioning (which has now been copied over to the new HD) to prevent linux from booting? Or alternatively, did M$ do something when it created the option of harddrive recovery programs?

---

### Post by cgjones on 2006-04-20
Have you checked the BIOS to see if the CD-ROM is set to boot first?

---

### Post by Sef on 2006-04-20
before burning, did you md5sum the disks?  

also could be the disks are bad too, if ur using the same bunch.

---

### Post by byenary on 2006-04-20
User a low burnspeed, or order the free cd's

---

### Post by mistergq on 2006-04-20
I am able to boot with any other CD - usually dos cds might I add such as the Seagate CD to set up the drive or Windows XP Installation disc (I tried one of my upgrade discs).

Also, the Ubuntu CD booted in my laptop and on another computer in the house.

---

### Post by cgjones on 2006-04-20
What is the current drive layout in the computer?

---

### Post by mistergq on 2006-04-20
To the hard drive controller is a primary hard drive 200 GB Seagate and a slave Maxtor 200 GB HD.  On the second controller is a DVD player as the primary drive and a dvd burner as the slave drive.  The CD was put in the primary drive, the same drive that is able to boot dos CDs.

---

### Post by cgjones on 2006-04-20
What happened to the 80 GB drive? Beyond that, nothing comes to mind right now. It sounds like all the drives are plugged in and jumped correctly. One thing you might want to try is to switch the DVD drives around so that the burner is master and the player is slave. I'm not sure if this will help, but I've heard before that if you have a burner and a regular optical drive on the same controller, the burner should be master.

---

### Post by mistergq on 2006-04-29
[QUOTE=cgjones]One thing you might want to try is to switch the DVD drives around so that the burner is master and the player is slave. I'm not sure if this will help, but I've heard before that if you have a burner and a regular optical drive on the same controller, the burner should be master.[/QUOTE]
CG - you were correct, to a degree.  The burner was the master, the optical was the slave.  both had cable select as the pin setup.  I flipped them, and decided to change the pin.  So I put the optical as master and the burner as slave.  And guess what, ubuntu distro boots right up.  Thanks for the tip.  BTW: it was a pain in the @$$ because HP has way to much case.  I had to take off both side panels, the front panel, and the top panel to get the front panel off.

---

