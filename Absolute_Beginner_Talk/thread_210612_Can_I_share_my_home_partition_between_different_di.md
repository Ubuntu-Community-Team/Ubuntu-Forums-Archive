---
title: "Can I share my /home partition between different distros?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-07-07
[LEFT]I've partitioned my hard drive into the following four primary partitions:
 
1.  / (Xubunutu root)
2.  Linux swap
3.  /home (created with the above Xubuntu install)
4.  / (Linspire root and home)
 
Is it possible to share my 3rd partition between Xubuntu and Linspire?  
 
I posted the same question on the Linspire forum and got an answer that there would be problems as Xubuntu runs Xfce while Linspire uses KDE.  I don't know why the choice of desktop manager would affect the ability to use a partition: I thought linux was linux and /etc/fstab was /etc/fstab irrespective of the distro.
 
Can someone explain it to me or, at the very least, confirm that the answer I got on the Linspire forum was correct?
 
Thanks.
 
P.S.  I don't want to install Kubuntu just to get around the compatability problem - if there is a problem, that is.[/LEFT]

---

### Post by crystal on 2006-07-07
[This thread](http://ubuntuforums.org/showthread.php?t=203271) might interest you.

---

### Post by jordanmthomas on 2006-07-07
It really wouldn't matter with the different environments.

The only problem you may encounter is that if you had the same program installed in both OSes, you may have problems with things pointing to the wrong places.  (One may be /usr/bin/something and the other may install the same stuff in /usr/sbin/something)

Your programs for that user would likely be flakey, so I wouldn't advise it.  But if you're up for a challenge keeping all that managed, go for it.

---

### Post by woedend on 2006-07-07
you can certainly try it, but i'd advise backing up all of the setting files(hidden) to the root directory...it will not take up hardly any room at all and may prevent a big headache.

---

### Post by n00b@linux on 2006-07-07
[LEFT]Thanks for the advice.
 
I think I will just mount my Xubuntu /home as a separate directory underneath /home when I'm working in Linspire.  That way I won't be unknowingly messing with any hidden config files on Xubuntu /home.
 
I've done the exact same thing with my Windows XP partition on a different PC of mine.  Why I didn't think of doing this in the first place I do not know.  Duh! ](*,) I'm such a n00b, lol.[/LEFT]

---

