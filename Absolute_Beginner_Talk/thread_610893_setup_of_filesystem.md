---
title: "setup of filesystem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by ARhere on 2007-11-12
I am setting up a file and print server using Ubuntu Desktop 7.10 and want to setup my families data for secure and easy Samba file sharing.  Before when the PC was windows, I had the types of data separated by drive letter...
c:\          ##OS and drivers
d:\          ##iSO images of disks, non-critical data
e:\          ##Generic Data Drive, important data
r:\          ##Raid mirror with critical data
 r:\PICS\
 r:\Tax_nfo\
 r:\Music\
 r:\Home\  ##the "My Documents" for each persons PC was mapped here to secure data even if the PC was blown away.
x:\          ##DVD Burner

Now that I am moving to Linux, I was planning on mounting "/home" on the RAID mirror organize like this...
Win way  ==> Ubuntu Way
--------------------------------
r:\Home   ==> /home/<user account>
r:\Tax_nfo ==> /home/taxnfo
r:\PICS ==> /home/pics
r:\Music ==> /home/mp3
e:\ ===>/home/data
x:\ ===> "don't care"

...and on another large HDD there would be two partitions, the first partition with...
c:\ ==> /, /boot, swap
...and the second larger partition with...
d:\ ==> /iSO

So, my questions are...
1.  Is this a good setup in the sense of assigning permissions of who can look at what?
2.  Is Linux going to be PO'ed at having non-user-account folders in "/home" ?  If so, I want both user data and important data on the mirror.
3.  Anything n00bishly stupid I am about to do here?

Cheers,
-ARhere

P.S.  I have been asking a lot of questions lately and I appreciate the patience of the "fully caffeinated" Linux users in this forum.:guitar:

---

### Post by cmnorton on 2007-11-13
Mapping users in this way seems completely reasonable. We're running a municipal collection system based on an application, also a Linux user with its own home directory, and everyone who uses that application is in the application's group.

I do not believe Linux should be happy or angry, as such, that you have placed a non-user account under /home, but you or someone else may get very confused, if you start thinking those are accounts. I would soft link it to a non-home directory, or make each "user" under home a real user.

---

