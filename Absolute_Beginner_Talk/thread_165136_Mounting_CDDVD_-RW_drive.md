---
title: "Mounting CD/DVD -RW drive????"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by lg3 on 2006-04-24
I have followed the new user guide....but I get this:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
do I need to edit my fstab?

Thanks for your help.

---

### Post by akudewan on 2006-04-24
I get this error when the CD is corrupt. try another cd maybe?

---

### Post by lg3 on 2006-04-24
okay i will try that thanks.

---

### Post by lg3 on 2006-04-24
Still get the same error....I also tried to install and run Kb3 (?) and installed fine but no go on the running. 

I think the problem is my CD-R/DVD-RW drive is not being properly recognized or something.

Thanks for the suggestions.

---

### Post by akudewan on 2006-04-25
Can you show your /etc/fstab file? Maybe it could give some hints.

---

### Post by Lord_Arithon on 2006-04-25
I'm having a similar problem...well it seems the same.  Infact let me explain my entire situation.

I am trying to install Linux on a Dell XPS Gen 2 laptop.  I had it all decked out with RAM and all that good stuff, and had all the latest things put into it at the time like NVIDIA 6800 and so forth.

Well I have tried installing Fedora, Suse, and now Ubuntu.  I keep getting the same problem where it tells me it wont mount the CD-ROM drive and it's because the disk wasn't in there(even though it was).....yet the the operating system loads fine up until that point.  I've tried everything, waiting till newer versions of Linux came out, and it kinda sucks that I can't get it....but anyway.  I'm having the same problem.

I checked out the new user guide as well and nothing is helping.

Aaron

---

