---
title: "Totally confused about CD drives and mounting"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-12
I am totally confused about mounting my CD drives.  I went to the book store to read about this because I couldn't find info on line.  The two books I looked at said this should have all been done automatically when I installed ubuntu.  Is this correct or not?

I have ubuntu installed on a computer with a CD RW drive and a DVD read only drive.  I can put my ubuntu CD in either of these drives and see the contents on Nautilus file manager, so I assume that means they are mounted.  Is that correct?

I wrote data to a new CD from a new laptop running windows XP.  When I try to read the new CD that I just wrote on the new laptop I get a message that says:

[B]Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
[/B]
mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

I open terminal and paste in "dmesg | tail  or so" and it tells me:

tail: cannot open `or' for reading: No such file or directory
tail: cannot open `so' for reading: No such file or directory

---

### Post by tc101 on 2007-01-12
I then put a blank CD in my CD RW drive.  I was able to write data to it.  I put the CD in the other computer running XP.  It read the CD and I was able to copy the data from the CD, but when I tried to write to the CD I got a message saying it could not write to it, make sure the CD is not full or write protected.

---

### Post by bscbrit on 2007-01-12
See this thread - the problem is not Ubuntu but Windows XP.


[http://www.ubuntuforums.org/showthread.php?p=1931926#post1931926](http://www.ubuntuforums.org/showthread.php?p=1931926#post1931926)

---

### Post by tc101 on 2007-01-12
Thanks for the link bscbrit.  I am still confused about the formating issues, but I now see that there is no problem with my setups.  That is a step in the right direction.  I have a lot to learn but so far it has been fun learning it.

---

