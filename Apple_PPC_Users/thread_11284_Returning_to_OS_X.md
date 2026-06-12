---
title: "Returning to OS X?"
date: 2005-01-15
forum: Apple PPC Users
---

### Post by nikopol on 2005-01-15
A bit of a long story so let's cut to the chase - a mate has ubuntu on his imac g4 (one of the early lamp style things) but has a sudden change of mind and now wants to dual boot with OS X. I advised him to start again from scratch - then partition from withing OSX then reinstall Ubuntu. 

But the OS X install won't find his HD anymore! is it because it is ext3? What can I do to make it see it again?

---

### Post by Down8ve on 2005-01-15
After you boot from the OSX install disc look for the Disk Utility under one of the menus.  Create one HFS+ partition for osx, then a "free space" partition for Ubuntu.

---

### Post by chascon on 2005-01-15
actually you need to create the Free Space first, then the HFS+ (OS X) partition else the partitions scheme collapses.

Top - Free Space
bottom - HFS+

---

### Post by nikopol on 2005-01-16
Hmmm - I'm not sure there is a disc utility in his version of the OSX install. Will check next time I swing by his place - in the meanwhile, he can learn how great linux is :D 
Thanks for the help chaps. Much appreciated  :cool:

---

### Post by chascon on 2005-01-17
The OS X installer CD has the disk utility.  When you fully boot for the CD, go to file? then disk utility or something like that for janguar (I can't remember what is is called in jaguar).  There you can partition under one of the tabs.  Just hightlight hd, and go to work.

---

### Post by nikopol on 2005-01-17
passed by his place and you were right it was there (But dissapeared later on in the installation process when it couldn't find the HD. Installed OS X for him again but didn't have time to install Ub. Will do that next time as the snow had started to fall pretty hard and I was worried about being caught in it!

---

### Post by mistic on 2005-01-20
about the partition thingy,

my linux-partition(ubuntu) is behind my mac osx-partition and it works fine here...

just so you know...

---

