---
title: "used wubi, unclean shutdown, totally stuck"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by amo310 on 2007-11-29
Well i have been wanting to try out linux for a long time now and when i came across ubuntu and wubi I thought it would be the perfect way to try it out. 

I installed it in windows, rebooted and was finally trying out linux for the first time. Then it froze, or I thought it did, and I held in the power button on my laptop to shutdown. Now when I start my laptop I am not presented with the choice to start xp or ubuntu. I am led straight to windows asking me to start in safe mode, normal mode, etc. When I pick any of these options windows begins to boot but it immediately goes to a blue error screen and everything restarts before I can even read it. 

My question is, where do I go from here? I don't have a recovery cd. The only reason I am able to write this post is because I made an ubuntu liveCD (I am able to mount the windows partition from this). I want to install Ubuntu permanently but I'd like to get my windows partition usable before I mess anything else up.

Can anyone tell me what is wrong? Thanks.

---

### Post by fineas on 2007-11-29
Try find a XP CD (borrow from a friend or :rolleyes:) and recover your XP installation. This seems to be the best option. 

Other possible solutions:
1) check here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
2)from an ubuntu live CD session, find boot.ini file, replace it with a backup version of it (if you have any) and reboot.
3) Go to [http://www.bootdisk.com/](http://www.bootdisk.com/) and try find how to create a boot floppy disk etc..., and boot your system with a boot floppy disk. Then, uninstall wubi from add/remove prgrams or from wubi's unistaller
4) Contact with your computer supplier and ask him about your problem 
5) Check at [www.microsoft.com](www.microsoft.com) (after all, it's a windows' installation)

Finally, do a memory test (ubuntu CD).Maybe computer has memory issues.

Hope these help:)

---

### Post by amo310 on 2007-11-29
i will try those out, thanks man.

---

