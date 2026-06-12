---
title: "move /home to a new partition"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by bcmiller on 2007-04-11
I did the default install of Ubuntu and now I'd like to create a new partition and make it my /home. 

I know it's possible but I forget how it's done now... 

I can make the partition fine I just want to be able to move the /home partiton..

My theory is that I can just copy all of the /home files to the new partition and then edit the fstab to look in /dev/sda2? (made that up) for my /home and then reboot. should that work?

The reason I want to do this is so I can tinker with a new distro on /dev/sda3?  and use the same /home and so I can keep my /home if I ever need to reinstall.  I intend on getting slackware going as my second distro to increase my linux knowledge.  Plus if I keep tinkering with my main OS (Ubuntu) I'll break it again like I always do.

thanks.

---

### Post by Shay Stephens on 2007-04-11
I tried sharing a home folder and it didn't work well at all.  So what I have done instead is make a data partition where all my stuff gets saved and the home folder just holds my program preferences and such.  So the data drive gets shared around but not the home folders.  I have not had any trouble since then.

---

### Post by ComplexNumber on 2007-04-11
you MUST use the live cd. the reason why is that you cannot do anything to the root partition whilst its still mounted and you're using it. you will just simply mess up your whole installation. 
op in the live cd, resize(if need be) the root partiton, add the home partition, then save it back to the MBR(you will be asked where you want to write the new partition details to).
then you can login and can move over all your stuff fropm your old home directory. it would probably be best if you changed your username.
never ever ever ever try to make alterations to your partition table or partitions  involving the root partition or home partition if its mounted (note whilst you are using it, its mounted).

---

