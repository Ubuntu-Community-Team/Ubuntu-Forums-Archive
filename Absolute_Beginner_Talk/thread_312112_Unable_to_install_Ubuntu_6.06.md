---
title: "Unable to install Ubuntu 6.06"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by spyder79 on 2006-12-03
I downloaded 6.06 DESKTOP files, burned the ISO to CD, all as per instruction.  I changed boot order to boot from CD drive.  I'm using a reasonably new PC with plenty of resources.

The problem is I am unable to start Ubuntu.  There is the initial screen, but it just hangs (nothing happens) after choosing any option, it just stays at the first screen.

I downloaded a second copy, just in case the first one was corrupted.  Then, I burned another CD at a very slow speed (I'm using the Image Burn utility) just in case that was a problem.  I even downloaded and burned the ALTERNATE file, just to check it out.  End result is that I've had no success.  I have tried this on two different computers, with the same result.

I should probably mention that I've owned a PC since a 386 was FAST, and managed to work through a lot of problems on my own.  I'm fairly computer literate, I think, but not real Techy, in the sense that I don't mess with partitions and boot sectors and modifying configuration files.  I've looked through the documentation briefly, but the information I've read seems to assume that installation will be a breeze because there's little mention of how to actually get everything working.  But maybe I've missed something.

I would love to try this OS, as long as it isn't a technical pain.

---

### Post by igknighted on 2006-12-03
Do these computers have ATI graphics cards?  Sometimes ATI cards don't work with the default graphics drivers.  Also, are you using a laptop?  Or any kind of a SCSI cdrom drive?  These things might all cause errors.  One final tip:  burn the iso's at like 4x, it takes a while but there are way less errors.  If none of this works try posting your hardware here and maybe we can find an incompatability

---

### Post by d3m0nz3y3 on 2006-12-03
i am having the exact same problem, as i posted in another post. Also i have a built in graphic card, computer is an asus laptop, and i dont know if i have a scsi cdrom... how do i find that??

---

### Post by spyder79 on 2006-12-03
Thank you!  I'm not sure about the graphics cards involved, but I think that one computer has that.  The CDs are burned at 4X speed.  Computers are both desktop models, not laptop.

I would attempt to retrieve hardware information, but it seems that I have some breakthrough on the computer that is the main target of installation (fingers crossed).  It seems to be going through an install routine right now, using the ALTERNATE disc. Not sure why it works now and not before. 

I'll post a follow-up based on the success or failure of the install.

> **igknighted said:**
> Do these computers have ATI graphics cards?  Sometimes ATI cards don't work with the default graphics drivers.  Also, are you using a laptop?  Or any kind of a SCSI cdrom drive?  These things might all cause errors.  One final tip:  burn the iso's at like 4x, it takes a while but there are way less errors.  If none of this works try posting your hardware here and maybe we can find an incompatability

---

### Post by spyder79 on 2006-12-03
Okay, at least I'm over the first hurdle.  Now, the installation procedure is stuck at the "INSTALLING BASE SYSTEM" screen.  It is at 6% progress, and stuck on "Retrieving:  libss10.9.8..."  I rebooted and it stuck at the same spot.  Would it be safe to assume that there is some data corruption on the disc?  I certainly hope not, since it takes me about 4+ hours to download the file.  Any suggestions?

---

### Post by Mimsy on 2006-12-03
Edit;
Seems we posted at the same time. And yes, that would be my would guess. I would try to download it through a friend with DSL if I were you... if you run a check on the CD, does it detect anything?

/mimsy

---

### Post by Voxxi on 2006-12-04
Did you check the MD5 hash of the .iso? That will tell you whether or not the .iso you downloaded is corrupted. A good program (for Windows) is [MD5 Summer]("http://www.md5summer.org/"). 

All you do is enter the filename into it, and it will output a lot of numbers/letters (Something like 2ccc1ec608040e6aac8913a016c31bed). This is the files "hash". A hash is basically a fingerprint of a file, so if you compare the hash of what you downloaded with the hash the site gives you and they don't match, it's corrupted.

Here is a list of hashes for the Ubuntu 6.06 .iso's:

b9a5be3a5858ade278d664d41310a4ab  
ubuntu-6.06.1-alternate-amd64.iso

6cb8582aa5615ed4616165743a0868d7  
ubuntu-6.06.1-alternate-i386.iso

0b5b3df02da3d9ed6f4ac482cf541f04  
ubuntu-6.06.1-alternate-powerpc.iso

50e3912c555f98f7bca56b2a0200b205  
ubuntu-6.06.1-desktop-amd64.iso

fb3af44c21f1f68cc25fda7edb8c1bd3  
ubuntu-6.06.1-desktop-i386.iso

502911770ad173dbe82c698379ed7d11  
ubuntu-6.06.1-desktop-powerpc.iso

8254b0f3696ed17c52a2cb59c9ebd2cc  
ubuntu-6.06.1-server-amd64.iso

5ad76d8b380ab5be713e5daa9ea84475  
ubuntu-6.06.1-server-i386.iso

6d1c3b5cb41661365b3db5cf12bb2836  
ubuntu-6.06.1-server-powerpc.iso

2ccc1ec608040e6aac8913a016c31bed  
ubuntu-6.06.1-server-sparc.iso

---

### Post by tuxcantfly on 2006-12-04
I think you burned your cd too fast. Try running "check cd for defects" from the ubuntu boot prompt

---

### Post by spyder79 on 2006-12-04
I have confirmed that my downloaded file is properly intact, but the CDs I burn have corrupted sectors even though I'm burning them at a very slow speed.  I'm going to buy some higher quality CDs today and try that.  I have been able to get part-way through the installation process though, which is a big improvement over my initial situation wherein nothing at all happened.  Then, I wasn't even able to run the Check CD utility.  So at least now I know now that I'll be able to install Ubuntu when I get a good CD.

Many thanks to all who jumped right in with pertinent information.  This is clearly a good group.

---

### Post by d3m0nz3y3 on 2006-12-04
as i posted earlier i was having the same problem. I burned the iso image at a low speed (4x) like mentioned here, and all worked well. I am loving the 6.10 alot. Hope this helps people who had similar problems.

d3

---

