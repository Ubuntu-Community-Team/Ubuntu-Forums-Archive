---
title: "[SOLVED] restoring ubuntu 7.10"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by bugged on 2008-03-21
good day to everyone.. i'm totally new to the ubuntu 7.10 experience.. being a total noon that i am, i installed ubuntu 7.10 in my laptop with vista os previously installed.. well it worked perfectly fine, thanks to the guides here.. however, i somehow modified the system when i tried to install/activate compiz-fusion.. i messed it up a bit.. is there a way to repair my Ubuntu 7.10? or can i reinstall this partition by logging in vista then just do a reinstall for my ubuntu? any help will be appreciated.. more power to you guys..

---

### Post by paydaydaddy on 2008-03-21
Post the specifics of what's happening. There is a good chance that it can be straightened out with a few terminal commands. If you just want to re-install, you should be able to follow the same procedure as for the original install.

---

### Post by bugged on 2008-03-21
thank you for the reply.. anyway, the problem that i want to solve is removing the compiz-fusion package and revert to the original compiz only settings that comes from the live cd.. the graphic performance is very lousy right now.. i just love how the original compiz-only perform.. but if i do the fresh install, will it overwrite the existing ubuntu OS? or will it create another partition? thank you sir and my apologies because i really am just a beginner..

---

### Post by bumanie on 2008-03-21
As long as you can boot into ubuntu, go to synaptic packet manager and type compizconfig-settings-manager into search and removing the things that are interfering with your graphics. If you don't know which ones to remove, do them one by one until you are happy with your graphics again.

---

### Post by bugged on 2008-03-22
i already tried disabling the compiz settings by choosing the first option in the appearance settings.. but still the display when i scroll down a page is choppy.. i hope you can help me sirs..:(
or if it is possible i just want to reinstall the while ubuntu OS from my dual boot system without messing my vista part..

---

### Post by Zalbor on 2008-03-22
What you're saying is strange, as if you've chosen "none" in the visual effects tab, compiz is not running at all (you're using metacity, the normal window manager). So if things are still choppy, then it can't be because of compiz...

In any case, if you just want to reinstall, it's as simple as booting from the live cd again and using the "install" program. You can use the same partitions you're using now, just tell it to format them (choose "manual" when it asks).

---

### Post by k3lt01 on 2008-03-22
> **bugged said:**
> i already tried disabling the compiz settings by choosing the first option in the appearance settings.. but still the display when i scroll down a page is choppy.. In a Windows system this would be a driver problem, so I would hazard a guess and say it could be a driver problem in Ubuntu as well.

What type of computer do you have? can you give us the specifications?

---

### Post by lswest on 2008-03-22
to prevent any confusion, he means at the partitioning step (i think it's step 5, not 100% sure though), you're meant to choose "manual" which will give you a list of partitions and mount points, choose your ubuntu partition (if you have one for the whole system, or if you have /home seperate doesn't matter, choose the main "root" partition) and edit the mountpoint to be "/" and choose "format" and ext3.  Then, if you do have a seperate home partition, find it and change the mountpoint to "/home" DO NOT FORMAT IT or all your data will be lost.

and yes, it sounds to me to be a driver problem too, can you post the result of ```
cat /etc/X11/xorg.conf
glxinfo|grep direct
lspci
```? it might help us figure it out. (run each line in a terminal)

also, what is the result of ```
aptitude search xserver-xgl
``` ? some people have issues with that package being installed.

---

### Post by bugged on 2008-03-22
wow, thank you guys for all the help.. i'll try everything posted here.. my hugs and kisses to evryone..:)

---

