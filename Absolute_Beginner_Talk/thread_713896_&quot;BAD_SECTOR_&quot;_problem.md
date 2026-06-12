---
title: "&quot;BAD SECTOR &quot; problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by sanjay_ahuja on 2008-03-03
hi everybody 

i am new to Linux and don't know much about it:(:(

i am facing bad sector problem in my hard drive
initially i had xp and Linux on my HP laptop
after i format it once,i was unable to install window and while installing Linux ,faced many problems.
later Ubuntu detected bad sector in one of my drive.and every time when i tired to install Ubuntu it gave error.:confused:

then i separated 30GB of space and left it unpartitioned.i was successful in installing it.however i am unable to recover that 30GB.is there some way to use that space which has bad sector.
:(
along with it another problem i started facing when i installed after leaving that 30GB space is one of my drive is always unmounted when i log on to Ubuntu.i have to manually mount it every time giving administration password. 
is there some way to solve my problem
please help me to get rid of it
thanks in advance:(:(

---

### Post by prshah on 2008-03-03
You can run the command "sudo badblocks -v /dev/hdaX" where X is the partition number that contains the suspected badblocks. If it finds any badblocks, you need to run fsck to mark them as unusable.

As for automounting your other drive, post your /etc/fstab, and I will tell you the changes required.

Cheers,
PRShah

---

