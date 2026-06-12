---
title: "[SOLVED] Grub Error 18"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by bioShark on 2008-03-15
Hi

For the beginning, I'm a n00b in Linux. I wanted to make a dual boot, WinXP - Kubuntu.
I have a 160 HDD, and after installing WinXP on 35G, primary partition, I've installed Kubuntu on the rest. Everything went smoothly, but now, when the installation was done, and the restart has been performed, I can't get to the screen where I can choose between Kubuntu & WinXP. This should have been the Grubs job, right? But instead I get the following error:

GRUB loading, please wait...
Error 18

And then the system halts....

Just for your info...I am writing from the LiveCD. So, any suggestion quickly would be appreciated, thx.

---

### Post by Shazaam on 2008-03-15
This might help........

[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by bioShark on 2008-03-15
Thanks for the link.
There is a lot o history inside :)). Anyway, I saw there a few hints about BIOS changes, which I will try them now. 
But the solution they recommend is to create a boot partition, right at the beginning of the HDD. Now, that;'s tricky. How do I do that? I mean, maybee there is a tool for partitioning here in the liveCD, but still, my HDD is already partitioned, and the first part is an NTFS with my WinXP. Now, if I manage to create the boot partition (by the way, how big should it be?) how do I install my GRUB loader there? Should I re-install Kubuntu? And at the end of the installation I should specify the path to the boot partition? 

Thanks.

---

### Post by Shazaam on 2008-03-15
Unless you know what you are doing I can't recommend adding a separate boot partition to an already installed system. Others here may disagree. See if you can resolve the grub issues first.
You can also try other bootloaders. GAG, EasyBCD (if you have Vista) are a couple that come to mind. You can also run Ubuntu from the XP bootloader too (search the forums).

---

### Post by bioShark on 2008-03-15
Hi

Right now I am taking the following action: Reinstall Kubuntu.
The difference this time will be: the partitions root & swap will be logical partitions (instead of primary as they were till now). I've read on an older post here at ubuntuforums that it helped others who were in the same situation as I am. If this doesn't help, I'll just loose 20-30 minutes of my life...no big deal. In any case, I'll get back to you.

---

### Post by bioShark on 2008-03-15
Hi

Yes, it SOLVED the problem.

So, solution:

(/) & swap = logical partitions instead of primary

Thanks

---

### Post by Shazaam on 2008-03-15
Great!
At the top you will see "Thread Tools". Please use it to mark this thread solved.
As an aside, my habit of always using logical partitions (except for Windows) has blinded me to some of the problems others have. Duly noted and bookmarked.

---

### Post by steveg944 on 2008-03-16
Thanks for the links Shazaam.

I have an 7 year old motherboard that did not support all of my 250GB HDD. Thanks to your link, I was able to resize the partition to less than 137GB and the Grub Error 18 is corrected.

Thanks again. And thanks to HermanZero too.

---

