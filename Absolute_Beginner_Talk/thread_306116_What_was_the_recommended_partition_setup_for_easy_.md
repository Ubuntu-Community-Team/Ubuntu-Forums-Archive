---
title: "What was the recommended partition setup for easy upgrades?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by SSB on 2006-11-24
I seem to remember there being a partitioning/mounting setup to use so that when you upgrade, you don't have to keep losing all your data. In fact I've completely forgotten what the 'best' partitioning setup is. I'm installing for the second time and I could use a reminder. Thanks.

---

### Post by taurus on 2006-11-24
/
swap
/home

When you upgrade or reinstall, just mount /home and don't format it.  Then, you can keep your all personal files and settings...

---

### Post by SSB on 2006-11-24
ok, thanks. Should I stick with the 256 mb swap, say, 10 GB home and the rest for root? Or should more be given to swap?

---

### Post by taurus on 2006-11-24
512 MB for swap is always a good and conservative choice.  ;)

---

### Post by SSB on 2006-11-24
last question, which should get more space? Home or root?

---

### Post by taurus on 2006-11-24
Depends on how much stuff you store in /home/$HOME!  How large is your harddrive?  10GB for / should be plenty...

---

### Post by turbojugend_gr on 2006-11-24
First of all, I believe the swap partitions to be best if they are double the ram's size. I fdon't know if that's a leftover since my windoz days, but I can recall, a Linux myth (to me at least) second that, any clarification is welcome.

As for the home partition, I give it all of the space that is left, after I have given 2xRam size for swap, 8-12 gigs to "/". After all that's where you store most of your data. Long story short, I second the above, with only slight modifications. ;).

---

### Post by bodhi.zazen on 2006-11-24
> **turbojugend_gr said:**
> First of all, I believe the swap partitions to be best if they are double the ram's size. I fdon't know if that's a leftover since my windoz days, but I can recall, a Linux myth (to me at least) second that, any clarification is welcome.

As for the home partition, I give it all of the space that is left, after I have given 2xRam size for swap, 8-12 gigs to "/". After all that's where you store most of your data. Long story short, I second the above, with only slight modifications. ;).

RAM X2 up to 1 Gb.

But... It depends on what type of applications you run and how much RAM you have....

---

### Post by turbojugend_gr on 2006-11-24
@bodhi.zazen: Thanks for the info, any link/reference, so I can define it better would be appreciated.

Cheers, TJ.

---

### Post by bodhi.zazen on 2006-11-24
> **turbojugend_gr said:**
> @bodhi.zazen: Thanks for the info, any link/reference, so I can define it better would be appreciated.

Cheers, TJ.

You understand this is an art? And controversial? I ALWAYS advise on the conservative side (RAMX2, 1 Gb max) as I figure if someone needs to ask I should give a conservative answer.....

Perhaps this is less then ideal, but it should prevent crashes.

Try these two sites for starters:

[Linux.com Allocating swap space](http://www.linux.com/guides/sag/swap-allocation.shtml)

[IBM  System Administration Toolkit: Swap space management and tricks](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

In the end it depends on # of users and type of applications you run.

---

### Post by qamelian on 2006-11-24
> **bodhi.zazen said:**
> You understand this is an art? And controversial? I ALWAYS advise on the conservative side (RAMX2, 1 Gb max) as I figure if someone needs to ask I should give a conservative answer.....
I do the same thing purely for the worst case scenario. That said, I have a gig and a quartet of RAM in my laptop, and while monitoring the swap partition, I have yet to see it used at all. I would still rather be safe than sorry.

---

### Post by turbojugend_gr on 2006-11-24
@bodhi.zazen: Thanks again, both links, are well-written, and they seem stable-based! Deeply appreciated, as it was bugging for quite some time now.

Best Regards, TJ.

---

