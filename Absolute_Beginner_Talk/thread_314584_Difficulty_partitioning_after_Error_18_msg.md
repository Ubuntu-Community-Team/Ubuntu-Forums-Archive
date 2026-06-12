---
title: "Difficulty partitioning after Error 18 msg"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by uubernoob on 2006-12-07
This is my first foray into the Linux world, and I read for two weeks before finally carefully burning a distro of ubuntu 6.06 and running it a few times off a live CD

Upon installing it and rebooting, I got the error 18 message, which means that the bios does not find the boot info in time, so it hangs. 

I read up about that and tried to repartition the drives according to the advice given (which I won't go into here, because if you understand this question, you don't need me to repeat what I don't understand).  Unfortunately, I have absolutely no idea how to partition them.  

I am hoping to get some very clear instructions on how to do so. The default partitioning did not work, and my attempts to manually partition have met with failure.

Looking hopefully for an answer,

Yours Truuly
Uubernoob ](*,) ](*,) ](*,) ](*,) 
god i hate brick walls](*,) ](*,) ](*,) ]

---

### Post by Bosonator on 2007-01-06
Well, to start with, can you describe your hardware? Specifically, what kind of chip does your computer contain? Also, does it contain a single hard drive, or more than one?

Secondly, you might try downloading and using ubuntu 6.10. It's newer and has an easy-to-use graphical installer.

If you have just a single hard drive and just want to go ahead with the 6.06 install, then here's what I think you have to do (this is just from memory, so sorry about anything that's not spot on!):

1. When you get to the partitioning menu, select "manually edit partition table". 
2. Create a primary partition and format it as ext3 (not ntfs or fat).
3. Select "/" (root) to be mounted to the partition.
4. Continue on with the installation.

---

