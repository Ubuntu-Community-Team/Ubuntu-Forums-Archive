---
title: "Recommended partition sizes for Gutsy"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-22
Hello all
I am formatting due to this:
[http://ubuntuforums.org/showthread.php?t=731333](http://ubuntuforums.org/showthread.php?t=731333)

I am now formatting my laptop. 
I am thinking of providing 17GB total to my linux, in which 15gb will be ext3 and 2gb swap, and the reast of the 160GB for /home
How should I keep the various partitions in the 15GB (Please mention recommended sizes for /tmp / etc.

---

### Post by Mustard on 2008-03-22
> **LinuxIsInnovation said:**
> Hello all
I am formatting due to this:
[http://ubuntuforums.org/showthread.php?t=731333](http://ubuntuforums.org/showthread.php?t=731333)

I am now formatting my laptop. 
I am thinking of providing 17GB total to my linux, in which 15gb will be ext3 and 2gb swap, and the reast of the 160GB for /home
How should I keep the various partitions in the 15GB (Please mention recommended sizes for /tmp / etc.

From what I have read on the forums the only really necessary 'extra' partition is the /home partition.  the /var, /etc etc...are not particularly useful for a desktop user.  Someone mentioned that /var was good for a server install because sometimes the log files(in certain situation) can become so huge that they would lock up the system when the root partition became full.  In that instance I can see the usefulness of a separate /var partition.  I havent found any need, so far, for extra partitions other than /home.

---

### Post by bhavi on 2008-03-22
I give 2 GB for /tmp and /etc and it works fine with me on a 80GB HDD...

---

### Post by sayakb on 2008-03-22
So what exactly would be the breakup?
/ = 13GB
/tmp = 1GB
/etc = 1GB
/home = Rest of the space..

Also, 15GB is enough of ubuntu, isnt it?

---

### Post by sayakb on 2008-03-22
@Bhavi
If you could come online...
Dave

---

### Post by Kiri on 2008-03-22
Why make extra partitions for /etc and /tmp?

I can understand the reason for /home, /, and swap. And in some cases /boot. But what is the advantage to having seperate /etc, /tmp?

---

### Post by Teber on 2008-03-22
my computer works just fine with just the partitions /home /swap and /root

---

### Post by Mustard on 2008-03-22
I guess its also possible for your /tmp to become so full that it locks up the system as well, unless its on its own partition.

---

### Post by sayakb on 2008-03-22
I guess it didn't work for me.. I made a 15GB / mountpoint, a 2GB swap mountpoint and a 135GB /home mountpoint partition. So after I booted to Gutsy, it froze everytime after the desktop appeared. So I just created one single partition for / and another 2GB for swap.. working fine till now..

---

