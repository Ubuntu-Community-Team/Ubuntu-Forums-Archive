---
title: "Ubuntu And Windows Service Pack 2"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-07-29
After over a week of constant reformats and reinstalls I've finally gotten my computer to dual-boot Ubuntu and Windows XP Professional.  What finally fixed it was doing yet another reformat and fresh install of Windows, then updating to service pack 2, and then installing Ubuntu.  Before I updated to sp2, I kept getting the BSOD with an UNMOUNTABLE_BOOT_VOLUME error.

I'm curious, since after almost 4 days of asking questions about what was wrong and only one person suggested I update to sp2, is anyone dual-booting with Ubuntu and XP Pro that hasn't updated to sp2?  And if not, then maybe it should be *some where* in the dual-boot instructions that you need to have sp2 installed?  Just wondering and suggesting....

Ash

---

### Post by T700 on 2006-07-29
I'm very happy it worked for you, but I've got to say that this is the first time I've ever heard of that trick!  Interested to see what others have to say.

Paul

---

### Post by magnoliablossom on 2006-07-29
It wasn't really a trick.  It was the consequences of being too impatient.  If after I had installed my new hard drive, I had gone ahead and got my Windows up to date like I *should* have, I wouldn't have wasted at that time for nothing.  But I use dial up and it takes FOREVER AND A DAY to d/l alllllllllll those XP updates sooooooooo....I found out the hard way that there are no shortcuts.  UGH!

---

### Post by MasterZ on 2006-07-29
Hello, 

I just wanted to share that I'm currently dual booting Ubuntu dapper with WinXP Pro SP1. 
It's working like a charm. I have already made 2 configs like that and I did not hava any problem... 

MasterZ.

---

### Post by magnoliablossom on 2006-07-29
I just don't get it then...I did everything the same this time as I did the last dozen or so times with the exception of updating Windows and I *always* got that @#$% blue screen! lol

---

### Post by T700 on 2006-07-29
> **magnoliablossom said:**
> I just don't get it then...I did everything the same this time as I did the last dozen or so times with the exception of updating Windows and I *always* got that @#$% blue screen! lol

In IT, that's called OOTWT, pronouced "ew wit" (One Of Those Windows Things).  I think the OOTWT process can explain many of my white hairs.

Paul

---

### Post by dave_567 on 2006-07-29
I'm not an expert on this but.....

It sounds like what you needed to do was something like this...

1) Install windows.
2) Make a copy of the MDR and save it.
3) Install Ubuntu with the grub loader.
4) Save that nwe MBR as well.

Now when you want to play with Windows installations that required a reboot just re-install the first MBR and do whatever you need.  When finished, reinstall the grub MBR to reset the system.

And always make a backup of the system before playing with the MBR.  It is fun, but it can make some unrecoverable situations. 

dave

---

### Post by Frank Golden on 2006-07-29
> **magnoliablossom said:**
> After over a week of constant reformats and reinstalls I've finally gotten my computer to dual-boot Ubuntu and Windows XP Professional.  What finally fixed it was doing yet another reformat and fresh install of Windows, then updating to service pack 2, and then installing Ubuntu.  Before I updated to sp2, I kept getting the BSOD with an UNMOUNTABLE_BOOT_VOLUME error.

I'm curious, since after almost 4 days of asking questions about what was wrong and only one person suggested I update to sp2, is anyone dual-booting with Ubuntu and XP Pro that hasn't updated to sp2?  And if not, then maybe it should be *some where* in the dual-boot instructions that you need to have sp2 installed?  Just wondering and suggesting....

AshOkay Magnoliablossom I just reread your original
post about this problem. I didn't see where you mentioned
not having SP2. It shouldn't make a difference but I guess it
did. It's been two years since the release of SP2 so I guess
we, myself included "***"umed you were trying to install XP
with SP2. Aside from the security issues SP2 fixed you really
should not consider an install of XP complete without SP2.
The following tutorial should help you "slipstream" SP2
into XP and create a new bootable install CD with SP2 already
integrated. That way any future installs will have SP2 included
automagically. You will need to download the SP2 "network
install" image as outlined in the following. I know you are on dialup. Perhaps you can go to library or something. I think the
file is about 260 MB or so. If you have a CD burner available
or a 512 MB memory stick, you can easily transport the file home.
I think M$ will send you a copy of the file on CD if you have
no other way of getting it. Perhaps they will swap your disk
out for the XP-SP2 one. At any rate you really should have a SP 2
disk whether you roll you own or not.

[http://www.tacktech.com/display.cfm?ttid=295](http://www.tacktech.com/display.cfm?ttid=295)

Sorry we missed that Magnolia, but in our defense I don't
think we/I considered the fact that not having SP2 was the
problem. Plus you really didn't mention it. Glad you got it all
figured out.
BTW, other than your time involved, which has value, I don't think
multiple formats of a HDD will significantly shorten the life
of a modern HDD. IMHO. Why would it? It may shorten you lifetime though.:smile:

Dave_367, GRUB is supposed to automagically manage dual boots
without user intervention, outside of choosing the OS to boot 
into. It works quite well on my dual boot (XP-SP2 + Ubuntu 6.06 LTS), without me having to juggle MBR's, I wouldn't have it any other way.

---

### Post by Lord Illidan on 2006-07-29
> **magnoliablossom said:**
> After over a week of constant reformats and reinstalls I've finally gotten my computer to dual-boot Ubuntu and Windows XP Professional.  What finally fixed it was doing yet another reformat and fresh install of Windows, then updating to service pack 2, and then installing Ubuntu.  Before I updated to sp2, I kept getting the BSOD with an UNMOUNTABLE_BOOT_VOLUME error.

I'm curious, since after almost 4 days of asking questions about what was wrong and only one person suggested I update to sp2, is anyone dual-booting with Ubuntu and XP Pro that hasn't updated to sp2?  And if not, then maybe it should be *some where* in the dual-boot instructions that you need to have sp2 installed?  Just wondering and suggesting....

Ash

I am on WinXp Sp 1...both Ubuntu and XP work together no problems!

---

### Post by magnoliablossom on 2006-07-29
Maybe then it's not so much as it needs sp2 as it needs at least sp1 because so far everyone had at least that.  I was using a disk I've had for years and I don't *think* it had any service packs on it.  But me in all my blondness (it's alright to joke about it since I *am* blonde lol) figured I'd by pass the big update until after I had every thing working to avoid having to d/l it multiple times.  At any rate, soon I won't have that particular problem anymore.  I ordered the sp2 cd off of M$'s website and should be receiving a copy of it within the next few weeks.

---

### Post by Frank Golden on 2006-07-29
> **magnoliablossom said:**
> Maybe then it's not so much as it needs sp2 as it needs at least sp1 because so far everyone had at least that.  I was using a disk I've had for years and I don't *think* it had any service packs on it.  But me in all my blondness (it's alright to joke about it since I *am* blonde lol) figured I'd by pass the big update until after I had every thing working to avoid having to d/l it multiple times.  At any rate, soon I won't have that particular problem anymore.  I ordered the sp2 cd off of M$'s website and should be receiving a copy of it within the next few weeks.
You should be able to integrate it into a "slipstreamed"
XP-SP2 CD using the link I gave you earlier. Or did you mean
they are giving/selling you a complete XP-SP2 CD. If all you get
is a disk with just Service Pack 2 it would serve you well to 
"slipstream" it to your existing disk.

---

### Post by dave_567 on 2006-07-30
Frank, 

I also have two double boot systems.  Grub handles normal operations great.  I can get to either operating system as needed.  But I have come across problems during some w$ installs that have not worked well with grub.  SP2 may be one of those cases.  I don't know as my copy of w$ has SP2 already on it.  It has helped to keep copy of originl the MBRs.  It is good for that last ditch recovery effort before a re-format.  Also when trying to save Ubuntu and a still place on a fresh install of w$.   

I had the older system loose the CD ROM during a Ubuntu installtion.  The CD hung during the instllation.  Good CD in a bad CD drive.  I recovered by re-installing the W2K MBR and replacing the CD drive.  Things went better after that.  When in doubt, keep a backup.  

dave

---

### Post by Frank Golden on 2006-07-30
> **dave_567 said:**
> Frank, 

I also have two double boot systems.  Grub handles normal operations great.  I can get to either operating system as needed.  But I have come across problems during some w$ installs that have not worked well with grub.  SP2 may be one of those cases.  I don't know as my copy of w$ has SP2 already on it.  It has helped to keep copy of originl the MBRs.  It is good for that last ditch recovery effort before a re-format.  Also when trying to save Ubuntu and a still place on a fresh install of w$.   

I had the older system loose the CD ROM during a Ubuntu installtion.  The CD hung during the instllation.  Good CD in a bad CD drive.  I recovered by re-installing the W2K MBR and replacing the CD drive.  Things went better after that.  When in doubt, keep a backup.  

dave

Hi Dave,
   You're right about backups. I handle things a little differently. I have
a spare HDD with an exact byte by byte copy of everything XP, Ubuntu and
all my data partitions etc. In the event of disaster I can recover in the time it takes to change drives. I even have the spare mounted in a spare
drive cage I purchased for just this reason. I also have my Ubuntu
install imaged to a separate USB HDD using partimage. If I mess up Ubuntu
I only need to install my image over the damaged one to be back in
business. Of course my scheme means that my imaged drives etc. are not
up to date. That is a small price to pay for not having to reinstall
everything. You can reinstall the MBR using the Windows install CD
and the fixmbr command from the recovery console, I think this is available
in W2K also.

It never occured to me to back up the MBR or GRUB.

I have Ubuntu 6.06 LTS installed on a Cruzer Micro 2GB USB thumb drive.
I don't even use the optical drive for install. Yes my BIOS supports
booting from almost everything. Course older systems probably can't boot from flash drives. I bet I could do the same with XP.
New project!

---

### Post by BadString on 2006-07-30
If you are still getting the BSOD "Unmountable boot device" errors you can boot with the Windows XP CD and go into recovery console. Then run a "chkdsk /f" 

This should fix your problems.

---

