---
title: "Very Slow performance."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Mustafa S. on 2007-09-24
Hey friends, need some help.
I installed ubuntu 7.04 i386 edition. Now the issue is that after the installation, my pc takes around 15-20 mins to boot up. Even after the boot up, the performance is really slow. The following is the config of my machine.

CPU: Intel Celeron 600Mhz
RAM: 384 MB
HDD: 40GB

Another problem is that my NIC is not getting detected and so i cannot setup the internet connection by entering my IP.

Can anyone help me out here? This is the first time I installed Linux and so i am a newbie to this stuff.

---

### Post by Imsati on 2007-09-24
>CPU: Intel Celeron 600Mhz
>RAM: 384 MB
>HDD: 40GB

Well, you partly answered your own question I think. 7.04, while very speedy on newer hardware, still has a lot of stuff packed into it for some older systems to run comfortably. Do you have access to a newer system you can install to and compare differences?

Also, if your CPU and RAM are that low, what kind of Mother Board do you have? Again, older technology may make it run slower.

The possible fixes... Upgrade to some newer specs, or try Xubuntu 7.04. Xubuntu is made specifically for older systems and uses less resources, therefore running much quicker on them compared to the Gnome version.

--Jay

---

### Post by Wiebelhaus on 2007-09-24
that sounds like a failing hard drive.

---

### Post by bigken on 2007-09-24
take Imsati advice and give xubuntu a try but dont waste money on upgrades
on such an old mobo

---

### Post by Imsati on 2007-09-24
> **bigken said:**
> take Imsati advice and give xubuntu a try but dont waste money on upgrades
on such an old mobo

By specs, I meant MoBo and CPU. Sorry for the confusion!

And thanks for the vote of support :)

--Jay

---

### Post by rsambuca on 2007-09-24
> **Mustafa S. said:**
> Hey friends, need some help.
I installed ubuntu 7.04 i386 edition. Now the issue is that after the installation, my pc takes around **15-20 mins to boot up**.

Even on that older machine it should not take anywhere near this long to boot up.  There is either a hardware compatibility problem or a bad installation.

---

### Post by bigken on 2007-09-24
what was the preformance like when you ran the live cd ?

---

### Post by adamklempner on 2007-09-24
Just for comparison, I have an old laptop that has:

Celeron 700 MHz
384 MB ram
40 GB hard drive

And that boots the Kubuntu livecd in 3-4 minutes.

---

### Post by vanadium on 2007-09-24
There is quite sufficient ram on that system and Ubuntu should run nicely. Another factor for causing the bad performance might be a badly configured network. You might try to run "top" to see whether there is some process that is taking many CPU cycles. For this, open a terminal window and type "top". By default, processes are sorted with decreasing CPU load, so you can spot which processes are using most of the time. Post these processes here.

---

### Post by Mustafa S. on 2007-09-25
Hey guys...the issue is resolved.There was some installation problem and I guess ubuntu was not installed properly. I reinstalled ubuntu and all is working fine.The internet problem is also solved. Thanks for the help everyone...

Cheers.

---

### Post by vanadium on 2007-09-25
Thus, it might have been the network after all ...

---

