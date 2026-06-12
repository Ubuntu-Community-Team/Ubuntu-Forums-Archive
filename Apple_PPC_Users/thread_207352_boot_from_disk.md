---
title: "boot from disk?"
date: 2006-07-01
forum: Apple PPC Users
---

### Post by shootdamonkey on 2006-07-01
i burnt the mac ubuntu disk, which is readable by the powerpc (beige powerpc g3) but i just cant figure out howto boot from the disk. I read in another forum about holding c during boot...no luck, then i read another about cmd+shif+alt+delete (or something like that) and still no luck. Any ideas?

Thnx

---

### Post by BoneKracker on 2006-07-01
Holding down c during boot should boot the CD (immediately after you hear the sound).  If that doesn't work, you probably made a bad CD.  

But try this first:

Reboot, and hold down ctrl+option+p+r until you've heard the boot-up sound a twice.  This will set the system back to defaults, after the last sound hold down c and it should boot from the CD.  If that doesn't work, you probably have a bad CD.  

But you could also try this:
Hold down "option" during boot.  Be patient.  A screen will come up showing each bootable "disk" (partition).  If you have MacOS installed, you'll see a disk with a Mac logo.  If you have Linux installed, you'll see a disk with a Tux logo.  If you have both, you'll see both, and so on.  If you have a bootable CD in the CD drive, you'll see a CD with the appropriate logo.  It takes a minute for everything to show up, so wait for the spinner to stop before you go clicking on things.  Then click on the CD and then click on the little "right-arrow" button.  That should boot from the CD.  

If you don't see a CD with a Tux logo, then check the image you downloaded (do an MD5 check).  If it's bad, download again.  If not, burn the CD again -- this time more slowly (4x or even 2x).  Also, make sure you are using media that's compatible with your drive.

---

### Post by shootdamonkey on 2006-07-02
tried all three options and none seem to work. Any way i can kinda refresh the system from inside 0S9 itself? or set it to boot from disk in os9?

---

### Post by BoneKracker on 2006-07-02
You probably have a bad CD.

Have you verified the integrity of the download?
Have you tried re-burning the disk.

---

### Post by linear on 2006-07-02
You said:
[quote=shootdamonkey]i burnt the mac ubuntu disk, which is readable by the powerpc (**beige powerpc g3**) but i just cant figure out howto boot from the disk.[/quote] 
The Beige G3 is an OldWorld Mac, and can't boot from a Linux CD. You need to look at the instructions [here]("https://help.ubuntu.com/community/Installation/OldWorldMacs").

---

### Post by BoneKracker on 2006-07-03
Sorry - I didn't know that.

---

