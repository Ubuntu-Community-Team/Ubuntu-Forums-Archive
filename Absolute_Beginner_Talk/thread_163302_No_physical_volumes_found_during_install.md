---
title: "No physical volumes found during install"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by kchukchukchu on 2006-04-20
Hello, everyone,

I still have not been able to install Breezy after more than 2 weeks of trying day and night and burning like 10 CDs and searching the web!

The following is the error message during the install, if you know what is going on,  I'd be very happy to hear from you. THANKS in advance:
======================================================
No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No volume groups found
reading all physical volumes, this may take awhile
selecting previously deselected package base-files
(reading database...0 files and directories currently installed)
unpacking base-files (from.../base-files_3.1.5ubuntu4_i386.deb)...
dpkg:base-passwd depends on libc6 (>=2.3.4-1); however
package libc6 is not installed.
setting base-passwd (3.5.10)...

.
.
.
CP: read error:  input/output error (times 5)

and then it goes on and eventually has dependency problems.
=======================================================

I have checked the MD5 sum of all of the CD images that I burn after they're burned and they turned out correct except the CDs would fail the integrity check on the installer during the install at either init.gz(1%) or linuximage.2. (9%) etc.  I burned at 8x, that's the minimum speed I could use.

My question is, do you think it's a CD problem or hardware problem?  Is it my CD drive (samsung SC140 CD drive)? 

I also tried linux noapic nolapic acpi=off, and it didn't work, and somehow if I turned DMA on, the computer could not even recognize there is a CD drive..

Please help, I dont' know what step is the best to take next.

THANKS!!!

Kay

---

### Post by taurus on 2006-04-20
You mean you can't burn anything slower than 4X!  Maybe you are experiencing problems with the media from burning too fast!  I think you should try to burn it at 4x and see if you can install from it again...

---

### Post by gondilon on 2006-04-20
you could go to the ubuntu website and request free cd's and try one of those instead. If nothing else, it would confirm wether it is a cd or hardware problem.

---

### Post by kchukchukchu on 2006-04-20
Thanks for your quick replies. 

I will try to look for a computer that will burn at slower than 4x. (I couldn't find one before and mine only burns as slow as 8x) and report back.


If you suspect other problems. Please let me know too.

---

### Post by Mustard on 2006-04-20
The fact that the ISO's are passing the md5sum check, but the CD's are failing the integrity check certainly points the finger at the problem occuring at the CD burn stage.  This could be hardware or media related ie your hardware is not burning them correctly/accurately, or the media it is burning to is faulty.  The hardware not burning them accurately could be solved by the above suggestions of burning at a slower rate or burning them on a different CD burner.  The media problem (if it is a problem at all), could be solved by getting a better brand of CD.

---

### Post by kchukchukchu on 2006-04-20
Hello Mustard, thanks for replying:)

But checked not just the ISO's md5sum, but I recopied the burnt image back to the harddrive and then check THAT sum.   I recopied the burnt CD to a windows machine and a mac machine and both passed that sum.. But then when I install it on my own machine, the CD woudl not pass the integrity check there...ONLY THERE.

what do you think? (I'm still trying to find a friend to burn at 4x for me)

Kay

---

### Post by Mustard on 2006-04-20
Hmm..well from that you would think the problem has to be on your CD drive.  I take it when you copied the ISO's (from the burnt CD) back to the windows and mac machines we are talking about different CD drives?

---

### Post by kchukchukchu on 2006-04-20
Hello, mustard,

Yes, I copied them back to 2 different machines, both NOT the one that I am installing in..  So, the problem should really NOT be in the CD if it passes the MD5 sum right?

THANKS for responding!

Kay

---

### Post by Mustard on 2006-04-20
[QUOTE=kchukchukchu]Hello, mustard,

Yes, I copied them back to 2 different machines, both NOT the one that I am installing in..  So, the problem should really NOT be in the CD if it passes the MD5 sum right?

THANKS for responding!

Kay[/QUOTE]

I would assume that yes.  If you copied the ISO from the CD back to the hard drive and ran an md5sum on the ISO sourced from the CD, then it seems to imply that the copy of the ISO on the CD is good.  With that eliminated as an issue, it seems to leave the CD drive itself as being the problem.

It would be an interesting exercise to copy the ISO from you current install CD, back to the hard drive, using your current problematic machine, and see if the copied ISO from the CD, passes the md5sum check. (assuming it has an operating system on it atm) :)

---

### Post by kchukchukchu on 2006-04-20
Hi Mustard,

Thanks for telling me your thought. that's what I thought too about the CD but then I thought it's still possible it's not good enough because I only burned it at 8x.  So, now i'd try the 4x.

I wish i haven't deleted windows on that machine to do the test, but I can't now!!!

wish me luck for the 4x,
Kay

---

### Post by catlett on 2006-04-20
Do you have another cd drive? If not how good of friends are these guys? You could borrow one of their cd drives, install it in your system and do the install. It's not that difficult to remove and install a drive. Just make sure you install the friends drive as the master in your machine if you can get his and you leave yours in. The computer boots to the master cd drive and will pass your slave drive if it finds nothing in the master (at least that is what happened to me before)

---

### Post by kchukchukchu on 2006-04-21
Hello Catlett,

Thanks for replying and for the suggestion.

I tried the 4x CD last night and it didn't work again :(, so now I am really suspecting the CD drive, and am really trying to get a friend for it.. 

otherwise, I don't know what I'll do, I dont' know if my old computer (HP Pavilion466Mhz) will take a very new CD drive, and I dont' know if I want to spend more money on this computer.. 

will report back,
Kay

---

### Post by jorn on 2006-04-21
You can't rely a 100% on the md5sum I have heard. Is there a possibility to try the burnt cd on another pc? An old cd-drive you can get for no money at least here in Denmark
Hope you find a solution. Ubuntu is hard to beat.
Cheers - Jorn

---

### Post by kchukchukchu on 2006-04-23
HELLO everyone!!

FINALLY, i got ubuntu server-installed!! 

Just want to report that it is the CD DRIVE problem.  It was an HP Pavilion 6535 with a Samsung SC140 CD drive. As soon as I changed the CD drive to a used 2000 made Sony 48x CDdrive, the install went smoothly. (even though when I read the ctrl-alt=f3 screen, there were still depency issues)

Here was another person with the same Samsung drive that caused the same problem:
[http://ubuntuforums.org/showthread.php?t=76316&page=3&highlight=debootstrap](http://ubuntuforums.org/showthread.php?t=76316&page=3&highlight=debootstrap)

So,thanks to everyone who has helped me along the way!  I just need to find a way to install the applications.  I dont' have internet so it seems hard.  But I'll search more and may need to ask you more:).

KAY:D

---

