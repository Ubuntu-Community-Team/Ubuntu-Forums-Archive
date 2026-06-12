---
title: "Ubuntu failing on Live CD"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by tnunn2 on 2007-08-15
Hi All,

I'm very new to Ubuntu.  Anyway, I just bought a new HP laptop two days ago, and I decided to install Ubuntu, just to see if I would like it.  The live cd loaded and displayed menu options.  So, I selected Start and install from the menu list.  Next, it started to load, however, it failed with the following error message.  

/bin/sh: can't access tty; job control turned off
(initramfs)


I searched the form for the resolution for this problem but with no avail.  I saw very similar situations but not exactly what I'm encountering.   Again, I'm very new to Ubuntu (1 week of experience) so I may be doing something incorrectly.  This may not be enough information but because of my inexperience in Ubuntu I'm not sure what else to put in the post.  So if I need to add anything else to the post to make it clear, please let me know.  


thanks,

trying to move away from Windows.

---

### Post by LordKthulhu on 2007-08-15
Tnunn2 - same deal, same message on Dell Inspiron 530 with Ubuntu 6.10 Gurus? (And let me go delete my post on the topic elsewhere...)

---

### Post by bapoumba on 2007-08-15
Thread moved to "Absolute Beginner Talk" support forum

---

### Post by LordKthulhu on 2007-08-16
tnunn2 - Could it be that your distro doesn't support SATA drives? From searching around, it does seem that it is my problem. Will update.

---

### Post by Hobo Joe on 2007-08-16
I've had this error before. Try taking out the disk and wiping it off and trying again.

Also, check for errors.

---

### Post by LordKthulhu on 2007-08-16
Done already. Same problem with Red Hat: installation starts OK, then can't seem to find the driver. Had no such issues with my old machine. Now, if there were a Linux distro that supports SATA from get-go...

---

### Post by amazingtaters on 2007-08-16
Are you using a fiesty live cd? Or if not, what version? Fiesty supports my SATA hdd just fine.

---

### Post by LordKthulhu on 2007-08-16
Dunno what tnunn2 is using, mine is EdgyEft. Do you reckon FF's SATA support is universal?

---

### Post by dphickey on 2007-08-16
I'm getting the same error as well.  I had 7.04 installed on this box once before and now I can't get it past this:

/bin/sh: can't access tty;  job control turned off


I'm using the Fiesty Fawn 7.04 live CD, on a Dell Latitude.
Anyone?

---

### Post by walktod on 2007-08-16
I'm having the same problem on an older pc.

Try this: [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

Didn't work for me, but should help you.

---

### Post by dphickey on 2007-08-16
That worked perfectly.  I'm back up and running.   Thank you.

---

### Post by tnunn2 on 2007-08-17
I finally successfully installed Ubuntu.  I had to use the alternate Ubuntu installation CD.  Once it was installed, from the command line I ran the following:

sudo apt-get update

sudo apt-get install ubuntu-desktop


I hope this helps!

---

### Post by LordKthulhu on 2007-08-17
Walktod - no luck so far. Will try Feisty today, maybe it'll go on right out of the box. Will update.

---

### Post by LordKthulhu on 2007-08-20
Success! Feisty installed on first try, without a hiccup. Yee-haw!

---

