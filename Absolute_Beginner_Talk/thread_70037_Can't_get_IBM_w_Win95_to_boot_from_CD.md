---
title: "Can't get IBM w/ Win95 to boot from CD"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by thinkergrrl on 2005-09-28
Hello all,

I'm really excited about Ubuntu, and am trying to do a full install on an old IBM laptop.  It's running Windows 95, which doesn't seem to have the F2 option to enter setup and get the thing to boot from CD.  And it isn't doing it automatically.

I can boot up in DOS mode and it tells me that several config.sys files are missing or corrupted.  Does that mean there's no hope?  I can get to a desktop and navigate around, but it does say that "A required .DLL file, MS09.DLL, was not found."

I'm sorry to post such basic questions but really appreciate any help.  I think these files were damaged when the person who retired the laptop tried to delete files in case it was going to be donated.

P.S.  I did try to Google this first, but didn't have any luck finding an answer.

---

### Post by Mustard on 2005-09-28
check your BIOS settings at startup to determine what order the system is looking at the boot devices in. Try hitting the 'delete' key during startup to get into BIOS settings.  It could be looking to boot from the hard drive, before it looks to boot from the CD.  Change the order so that it checks the CD before it checks the hard drive.

---

### Post by thinkergrrl on 2005-09-28
Thank you!!  The delete key worked!  I had tried F2, F8...you name it.  

I appreciate your help with such a basic question.

Off to finish the install!!

---

### Post by Mustard on 2005-09-28
No problem.  Good luck with the install. :)

---

