---
title: "dual boot ubuntu and mac ibook g4 powerpc"
date: 2009-01-31
forum: Apple Hardware Users
---

### Post by krazykeith250 on 2009-01-31
hello, I was thinking of installing ubuntu 7.04 on a partition that I would make in disk utility.

So I would choose the partition that I made and install ubuntu on it, but because it is a powerpc, will the computer see both partitions at start up if I hold down the option key?


I'm doing this on a ibook g4 1.33Ghz 1.5gb ram

---

### Post by tiresia on 2009-01-31
Did you already installed MacOSX on your g4?
You can install also 8.04 or 8.10

---

### Post by krazykeith250 on 2009-01-31
Ya I've had mac on it for a while, I just did not know if the computer would see both partitions if I held down the option key at start up.  also is 6 gbs too small of a partition?

---

### Post by tiresia on 2009-01-31
> **krazykeith250 said:**
> Ya I've had mac on it for a while, I just did not know if the computer would see both partitions if I held down the option key at start up.  also is 6 gbs too small of a partition?

Yes, the computer will see both partition (but you won't need to press the option key each time, yaboot, the linux bootloader for powerpc will ask you  wich system you want to boot from). 

6 GB can be enough, it depends what you want to do with it. If you have some data, it can become too small.

If you want just to test Ubuntu, you can try the LiveCD (8.04). How much RAM do you have? 

If you want to install again MacOSX and Ubuntu, start installing OSX and leave a second partition free for Ubuntu.

---

### Post by mkvnmtr on 2009-01-31
If you wish to install Ubuntu on your mac you can use disk utility on your mac install disk to get your hard drive ready. You can't do it from a mounted mac os. I would recommend that you defragment first. Then with disk utility shrink your mac partition. The install will be easier for you if you don't form another partition with disk utility. Just leave it as free space. 6Gb is enough but if you have the space 10 is better. Then exit the install disk and check that your mac os if fine by booting into it. Then you can restart with the live disk and install into the free space you created. when you get to the type of install choose to install into the largest free space. This will form the partitions you need for swap, boot and root without changing your mac os. If at any time during the install up to the point of formating you are not sure you can back out to the desktop to use Firefox to come to the forum to ask questions.

---

### Post by krazykeith250 on 2009-01-31
If you want just to test Ubuntu, you can try the LiveCD (8.04). How much RAM do you have? 

ya all I want to do is test it out and have fun with themes and effects and I have a gig and a half of ram

---

