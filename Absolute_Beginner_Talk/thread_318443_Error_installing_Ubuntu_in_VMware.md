---
title: "Error installing Ubuntu in VMware"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by linuxn00b73 on 2006-12-14
Hello to all!
 I wanted to give ubuntu a try first. Actually I'm trying 3 different linux distros. I'm completely new to linux, used unix a couple times, but I've gotten so annoyed with M$ I figured it would be a good time to learn.

   Anyways, I've been having a lot of trouble with installing ubuntu. First, having to use the liveCD to install takes way too long. There seriously has to be a way to install w/o having to load all that, if not it should be included in the next update. It crashed several times ](*,) 

    When I finally got going, I can only make it to the select a disk screen, the progress bar starts for the partitioning thing and it freezes and a tip shows up from VMware saying 
"Your virtual machine has sent an ATAPI (CD_ROM) command that is supported only when programming the drive via DMA. You will need to configure your guest operating system to use DMA when communicating with DVD/CD-ROM devices.
Note that some operating systems will report DMA is available without actually using it. In those cases, normal CD-ROM operations will still be available, but special features will only be available if you reconfigure the virtual device as a SCSI device."
Been trying to figure this out for 3 hours now. Thanks for any help.

---

### Post by marx2k on 2006-12-14
Could you please clarify if you're trying to install inside of VMWare? I'm somewhat confused.  I would think that if you're doing it in VMWare, you could just use an ISO of the LiveCD versus the physical CD itself- would definitely take less time.

---

### Post by Bachstelze on 2006-12-14
First off, I suggest you try the Alternate CD instead of the "Desktop" one. Then, if you still need to manually enable DMA, [here](https://help.ubuntu.com/community/DMA)'s how to do it.

---

### Post by linuxn00b73 on 2006-12-14
-Marx2k
I'll give that a try and see if it helps. I ususally install from the CDs just fine so I didn't even think of it.
  Thanks

-Hymntolife
Aargh another download! Oh well. Thanks. Should be able to get his going now. Can't wait.

---

