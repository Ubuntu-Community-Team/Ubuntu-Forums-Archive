---
title: "Installation Question"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by luke949 on 2007-04-14
Hi, I currently have windows xp and I have 5 hard drive partitions.

(1) 10gb - Windows Files
(2) 50gb - Programs
(3) 50gb - Entertainment Files
(4) 50gb - Misc.
(5) 15gb - (nothing atm)

I was wondering if I can install Ubuntu on an entirely different partition than Windows.
For example I want to install Linux on my 5th hard drive, the one with 15gb. Is this possible? And if so, can someone please explain to me how to do it? I tried it by myself and I got to the "Prepare mount points" window and I just got lost from there.

btw I want to dual boot.

Thanks a lot guys.

---

### Post by freebird54 on 2007-04-14
Certainly is possible - even recommended!  IS the unused space currently empty - or just not needed?  If it is 'unused space' in the partition table, the automatic setup will do it for you.  If not, better to use the manual partition choice, and mark out 2 partitions within it - a small (512Mb to 1Gb) swap space, and one marked for use as /  (that means the root of the filesystem)  Make sure those 2, and ONLY those 2 are marked for formatting.  It will automatically handle the rest for you - including making your Windows drives visible.

Please post again if not clear.  You might also want a look at:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

to understand what you're tring to do!  Good luck!

---

### Post by luke949 on 2007-04-14
The unused space is empty and I will give this a try thanks a lot!

---

### Post by N Clement on 2007-04-14
Please also note that  right now you only have 4 partitions--the unused space doesn't count.

Also, 4 is the maximum number of *primary* partitions allowed on a hard drive.  To get around this limitation, you can use an extended partition which can have other partitions nested inside of it.  This is still a problem because an extended partition still counts as one of your 4 allowed primary partitions, so one way or another, you have some file shifting to do :wink:

---

