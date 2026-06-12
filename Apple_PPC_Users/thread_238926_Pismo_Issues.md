---
title: "Pismo Issues"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by dcollamore on 2006-08-18
I have a 'Pismo' (G3 400MHz, Firewire) notebook that I just picked up for a song, but I'm having some difficulty booting an install cd.  I've tried factory pressed Dapper and Breezy, both LiveCD and Install; I've tried the 'alternate' install for dapper (downloaded ISO, burned at 1x to TDK, Sony, AND Verbatim media; checksum matches on all three).  I've zapped the PRAM and NVRAM.  The closest I get is if I go to the boot device selecter it sees the Ubuntu disks as bootable, but it just dumps me to an openfirmware prompt and goes nowhere from there.

Before you ask me if it's a bad optical drive, I can boot to and install OSX or YDL with no problems, every time.  It seems to be Ubuntu specific (however that would work).  I use Ubuntu exclusively for my in-home server, x86 laptop, and desktop, so I would like to go the same route on this beautiful Pismo; I just seem to be missing something.  Anybody with similar experience, or maybe some ideas?  Thanks in advance!

---

### Post by avtolle on 2006-08-18
Here [http://www.ubuntuforums.org/showthread.php?t=236543&highlight=Pismo](http://www.ubuntuforums.org/showthread.php?t=236543&highlight=Pismo) is someone who had success, if you haven't seen it. I have a question: how much ram do you have? I'm unfamiliar with your computer, thus the question. Best of luck.

---

### Post by dcollamore on 2006-08-18
Thanks for the link and speedy response...I've tried the alternate install as per that thread, but no luch there either.  The system has 512MB of RAM...I'm beginning to think I have a lost cause on my hands here.

---

### Post by dcollamore on 2006-08-20
Any ideas before I give up???

---

### Post by avtolle on 2006-08-21
One last thought, based upon my unfamiliarity with your hardware; is a "Pismo" an Old World Mac? If so, you need to use Boot-X (passing the kernel to the appropriate file), booting from the Mac OS, then choosing Linux. I have no experience doing this, just have read a number of threads about this. HTH.

---

### Post by gobabushka on 2006-08-21
nope the pismo is a new world machine. ive got the same problem, and ive tried all of those things. my only difference is that im not using an apple drive.

---

### Post by avtolle on 2006-08-21
gobabushka; thank you for the information. If both of you downloaded the 6.06.1 iso, and burned it (the iso) as an image, then I'm currently out of ideas. Perhaps someone else can assist.

---

### Post by tidris on 2006-08-21
Have you tried booting from the CD by holding down the C key instead of the Option key? It works on my 500 MHz Pismo.

---

### Post by kadymae on 2006-08-22
Just to doublecheck -- you are holding down the C key upon boot to force a boot from the optical drive?

Just to triplecheck -- you are using the [PPC ISO]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-powerpc.iso"), right?

---

### Post by tidris on 2006-08-22
> **kadymae said:**
> Just to doublecheck -- you are holding down the C key upon boot to force a boot from the optical drive?

Just to triplecheck -- you are using the [PPC ISO]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-powerpc.iso"), right?

Yes and yes, and I burned the iso into a CD, not into a DVD.

---

### Post by kadymae on 2006-08-22
I've never done this, but ...

... the only other thing I can suggest you try, and you will need access to another Mac for this, is to try a Target Disk Install.

Turn your Pismo off and run a FireWire cable between it and another Mac.  Turn on the Pismo and hold down the T key as it boots, as soon as you see the FireWire symbol on the desktop, your Pismo is now convinced that it's an external FireWire drive.

Put the Ubuntu disk into the other Mac and boot with the C Key down.  When asked which drive you want to install on, pick the drive size that corresponds to your Pismo.

Good Luck.  No gurantees that this will work.

---

(Or you can just run OS X.  ;))

---

### Post by avtolle on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=219584&highlight=Target+Disk+Install](http://www.ubuntuforums.org/showthread.php?t=219584&highlight=Target+Disk+Install) post #5 has a suggestion on how to attempt this.

---

