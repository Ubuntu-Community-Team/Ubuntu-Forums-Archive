---
title: "I might have screwed up big time installing Ubuntu"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by srinv9 on 2007-12-10
Hi,

   I had a not so old one and half year old laptop Toshiba A105 series with 1GB Ram and 120 GB hard drive. I took a liking to ubuntu and started installing ubuntu, while performing 4th or 5th task of installation like doing partitioning or something, my laptop dropped from my stop gap desk and fell down, stopping my system. From then ubuntu doesnt load from Live CD nor if it had installed on my laptop it doesnt even load from hard drive too. My windows software also looks like its gone, Nothing works for me except the ubuntu menu when we load the live Cd to start or install the software, memtest, etc. Appreciate if someone could help me guide what should I do.

thanks
Sri

---

### Post by ib.lundgren on 2007-12-10
Hey!

When you boot up with the Live CD, choose to test the cd for defects and see if the cd is still intact. Have you tried doing the safe start with the LiveCD?

If it broke during the partitioning of your hard drive Ubuntu hadn't been installed yet. Do you remember what option you chose when partitioning? becuase you might have formatted your windows partition...Did you chose "Use whole disc" or "Resize disc" or what?

In case you broke the LiveCD, formatted over your Windows partition I would recommend getting a new LiveCD or perhaps a Windows Installation disc incase you don't have any extra live cds...

---

### Post by Presto123 on 2007-12-10
This will be some helpful information if you could post it:

Were you partitioning it for dual boot? Or were you wiping the Windows partition?

**Edit: lb beat me to this question.**

---

### Post by srinv9 on 2007-12-10
> **ib.lundgren said:**
> Hey!

When you boot up with the Live CD, choose to test the cd for defects and see if the cd is still intact. Have you tried doing the safe start with the LiveCD?

If it broke during the partitioning of your hard drive Ubuntu hadn't been installed yet. Do you remember what option you chose when partitioning? becuase you might have formatted your windows partition...Did you chose "Use whole disc" or "Resize disc" or what?

In case you broke the LiveCD, formatted over your Windows partition I would recommend getting a new LiveCD or perhaps a Windows Installation disc incase you don't have any extra live cds...


I chose whole disk for partition. I havent tried testing the CD, will it get corrupted or something by any chance by any actions.

---

### Post by thelatinist on 2007-12-10
Hmm.  This is interesting.  First of all, by choosing to use the whole disk you have erased your Windows installation.  You should not expect to be able to boot into Windows any more.

As for the problem booting from the Live CD, unless there is physical damage to the CD (which I wouldn't expect from a fall with the CD in a drive), it should be able to boot into the Gutsy Live CD just like it did before.  I wouldn't be at all surprised if a fall during partitioning would mess up the partition table on your hard drive, and a fall can even break a hard disk, but those should not affect booting from live CD.  I second everyone else's suggestion of testing the Live CD and, if possible, trying another bootable CD-Rom (Windows or another Ubuntu Live CD is you can find/burn one).

---

### Post by srinv9 on 2007-12-10
> **thelatinist said:**
> Hmm.  This is interesting.  First of all, by choosing to use the whole disk you have erased your Windows installation.  You should not expect to be able to boot into Windows any more.

As for the problem booting from the Live CD, unless there is physical damage to the CD (which I wouldn't expect from a fall with the CD in a drive), it should be able to boot into the Gutsy Live CD just like it did before.  I wouldn't be at all surprised if a fall during partitioning would mess up the partition table on your hard drive, and a fall can even break a hard disk, but those should not affect booting from live CD.  I second everyone else's suggestion of testing the Live CD and, if possible, trying another bootable CD-Rom (Windows or another Ubuntu Live CD is you can find/burn one).


   Well my laptop fell from my lap on the carpeted area. There not much physical damage I see on the CD and also to my laptop. I am really not sure what I should be doing as I am totally new to linux and hence to Ubuntu. For now I am downloading a new .iso file rather than order another free CD. appreciate any tips before I start reinstalling. 

   I always get some command line errors of I/O whenever I try to start or install again ubuntu

  Forgot to mention, currently that laptop is running memtest86 which came with the laptop and already 6 passes without any errors. I am really not sure how long should I run that memtest. Should I stop that one and rerun ubuntu

---

### Post by thelatinist on 2007-12-10
> **srinv9 said:**
>  I always get some command line errors of I/O whenever I try to start or install again ubuntu

If it is giving you error messages when you try to install, you will need to post those messages here for us to give you any help.

---

