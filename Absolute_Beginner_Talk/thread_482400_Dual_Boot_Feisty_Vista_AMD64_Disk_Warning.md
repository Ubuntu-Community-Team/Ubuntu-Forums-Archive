---
title: "Dual Boot Feisty Vista AMD64 Disk Warning"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by rjohnsonxx00 on 2007-06-23
I installed 64bit Feisty Fawn on an HP Vista Home Premium workstation with no problem.  Worked fine  for over 1 month.  Now, on boot, I get a nasty message:  "ST3250820AS (model of disk drive): Hard disk failure  is imanent.  Please back up your hard drive and have it replaced."  Anybody get this?  Virus?  Real warning?  Help appreciated.

Richard Johnson
rjohnsonxx00 at yahoo.com

---

### Post by DBStevens on 2007-06-23
What is issueing the message?

Your Bios or Vista or Grub or Linux ?

---

### Post by DBStevens on 2007-06-23
My bet is that your 250GB Seagate SATA  SMART equiped hard drive is telling the bios I think I'm having trouble.

---

### Post by rjohnsonxx00 on 2007-06-23
I agree that the seagate HD is sending the message.  It occurs during the bios part of booting, but once I found it  on the screen after defragmenting.  The defragmenting came when I contacted HP for service.  The dude suggested that defragmenting might set the HD at ease.  No  such luck; got message after finishing, seemingly with success.  Also, Vista runs no worse than expected (running in overshoes).  Question:  what to do now?  Call HP back?  Any thoughts?

Thanks!

-- Dick Johnson
rjohnsonxx00 at yahoo.com

---

### Post by DBStevens on 2007-06-23
Who has warranty responsibilty for it  HP, Seagate, or is it off warranty (that means you)? 

There should also be a piece of software that allows you gather additional diagnostic information.  

It isn't a virus, it is a potential loss of the HD and the data that is on it.

It wouldn't hurt to talk with Seagate if you get no where with HP.   I don't have now nor have I ever had hardware from either company so I have no idea if they have decent service or not.

In any event with out further information I wouldn't trust the drive to be reliable.

---

### Post by Jimmyfj on 2007-06-23
> **rjohnsonxx00 said:**
> I agree that the seagate HD is sending the message.  It occurs during the bios part of booting, but once I found it  on the screen after defragmenting.  The defragmenting came when I contacted HP for service.  The dude suggested that defragmenting might set the HD at ease.  No  such luck; got message after finishing, seemingly with success.  Also, Vista runs no worse than expected (running in overshoes).  Question:  what to do now?  Call HP back?  Any thoughts?

Thanks!

-- Dick Johnson
rjohnsonxx00 at yahoo.com

I have experienced the exact same thing on my 200 GB Maxtor SATA drive - I even tried updating my BIOS but the message kept showing at boot so I tried to disable the S.M.A.R.T function in BIOS and the drive still spins as always, and has done so for two years now - This isn't the first time I've seen the S.M.A.R.T function fail in reading a drive correctly - Whether to swap the drive is a matter of trust - Either the drive dies or it keep spinning, I for one don't trust the BIOS S.M.A.R.T function having seen it fail on more than one computer. I do not believe that the S.M.A.R.T function is able to distinguish between a  possible hard drive fault and a corrupted file system. If you trust that the drive just might not have any faults you could try another defragmentation program:

[http://www.oo-software.com/home/en/products/oodefrag/](http://www.oo-software.com/home/en/products/oodefrag/)

Then check if the BIOS still reports an error on bootup.

---

### Post by DBStevens on 2007-06-23
Skinny on S.M.A.R.T 

[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

### Post by Jimmyfj on 2007-06-23
> **DBStevens said:**
> Skinny on S.M.A.R.T 

[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

As I already said above I do not put my faith in the S.M.A.R.T function, and here's why:

"This article has covered the basics of smartmontools. To learn more, read the man pages and Web page, and then write to the support mailing list if you need further help. Remember, smartmontools is no substitute for backing up your data. SMART cannot and does not predict all disk failures, but it often provides clues that something is amiss and has helped to keep many computing clusters operating reliably."

---

### Post by DBStevens on 2007-06-23
I don't think I said I put my faith in S.M.A.R.T or for that matter most technology, however after having lived in the trenches for close to forty years you ignore any error reporting system at your own peril.

I've seen error detecting circuits indicate an error when none was present, and I've seen errors occur without  being detected at all.

However one investigates all reports of errors by error detecting systems to determine if an error in fact exists.

All data should be backed up and those backups should be verified by reloading them and checking the reload for correctness.

---

### Post by rjohnsonxx00 on 2007-06-24
Thanks for the help, folks.  I will back up my HD to both a twosided DVD and also to a USB external drive.  Then, I will lean on HP to solve the problem.  The machine is 2 months old, and under full  warranty.  HP should know anything seagate knows or, at least, take responsibility.  I go back 35 years as an HP customer, so  I  know how to work with them.  I appreciate the information you contributed and, as I gain experience with Ubuntu, hope to  pass it on.  I have both Edgy and Feisty working now; Feisty is the strong favorite, esp. with the AMD64 support.  Verrrrryyy fast!  :)

Cheers!

rjohnsonxx00

---

