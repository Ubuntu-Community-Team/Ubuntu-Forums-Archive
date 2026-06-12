---
title: "Problem booting after installin Ubuntu"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by meinme on 2008-03-16
Hi 
i have an old 333Mhz Celeron PC.
I've XP professional running on it. Recently i installed Ubuntu in it.
I was able to work with Ubuntu in it yesterday.
The dual OS worked really fine.
Today when i tried to boot my PC it dint go to the opening screen at all.
The first screen displaying "ASPIRE" comes, followed by the sys specs screen, and then again the same ASPIRE screen.
It doesnt boot at all.
I'm not able to use both the OS's.
What am i supposed to do??

---

### Post by Diabolis on 2008-03-16
Insert the live-cd and reinstall grub.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Bölvaður on 2008-03-16
well there are few things you can do, but the easiest I can think of is reinstall ubuntu, as you probably haven't done much work on it yet any way.

Im guessing MBR has been changed so reinstalling would solve it.

---

### Post by Ub1476 on 2008-03-16
You mean you don't even reach GRUB (boot-loader/starts OS after BIOS has been loaded)? Have you tried to start with a Linux/Ubuntu live cd? Might be a problem with BIOS, but I doubt I can help you then..

---

### Post by meinme on 2008-03-16
It doesnt boot at all. Something like Initialising GRUB flashes on the screen and then it reboots again.
I dont kno what he prob is cos i'm new to Ubuntu, as well as computers.
I'm a beginner.
So do help me with all the steps.

---

### Post by Diabolis on 2008-03-16
if "initializing grub" appears, it means that grub loaded and picked an operating system by default without giving you any chance of picking it. Thats good news, grub is messed up, you just have to reinstall it.

Insert the live-cd and install grub from there. Open a terminal and type:

```
sudo grub
```

then follow the link I posted above.

---

### Post by Ub1476 on 2008-03-16
Then there is a problem with Grub. I suggest you try Diabolis suggestion. If you have another computer available, you can burn [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download") to a CD and it can reinstall Grub for you too (I suggest you have a CD of this tool always available, it's really great).

---

### Post by sandysandy on 2008-03-16
have a look at this link on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

