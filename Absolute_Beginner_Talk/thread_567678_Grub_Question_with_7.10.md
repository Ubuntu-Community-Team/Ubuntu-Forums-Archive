---
title: "Grub Question with 7.10"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by BlueScotch on 2007-10-04
I just installed the gutsy beta to to my laptop to try out the new restricted drivers feature that initially turned me off to linux (broadcom wireless card).  I now have ubuntu up and working correctly on a wireless connection, and I am quite happy.

The one problem is it seems the new Grub that was installed (Previously I only had win xp on one partition) cannot see my windows partition.  I am not given the choice to boot Windows XP, although I made sure not to delete that particular partition when installing gutsy.  Is there a way I can force GRUB to recognize my windows xp partition?  IIRC the windows partition is something like /media/windows or something like.  I think it is like two directories deep.

Any help is greatly appreciated

---

### Post by louieb on 2007-10-04
If your correct and xp is still there. Remember Gutsy is beta and sometimes turn left when it should have gone right. You just need to add an xp entry to /boot/grub/ menu.lst. Do a forum search on boot windows. or [Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

