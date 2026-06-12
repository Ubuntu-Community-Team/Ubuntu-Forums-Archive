---
title: "Damaged Feisty?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Sanctus Messor on 2007-09-27
I am not sure what is wrong with my distro. I am using Ubuntu Feisty though I did integrate the needed Nvidia drivers into the kernel. It worked fine for a good while and then just recently crapped out on me. GRUB will load and from there I have the usual options. When I tell it to boot the screen goes black and nothing happens. My keyboard is backlit and has only lit up when and while Feisty was booting; point is, the keyboard back lights come on during the black abyss. I let it sit there for 15 minutes to see if it would work itself out, but it didnt. I can boot by running the recovery from GRUB and that is the only way to get into my Feisty. Any ideas?

[Note] I am new to Linux, integrating the kernel was done by a friend who has been using Linux for the past 8 years.

---

### Post by PmDematagoda on 2007-09-27
Why on earth did you get a kernel integrated with the Nvidia drivers? The monolithic design is one of the reasons Linux is so  stable, if you start integrating stuff to the kernel, then you are going the Windows way which is not very stable at all.

---

### Post by madoracle on 2007-09-27
Same question - why did you add the NVidia drivers? Ubuntu has native support for NVidia chipsets. But most likely the error is in the config file for X. Have your friend come fix it, since his adding those drivers prolly screwed it up in the first place.

---

### Post by Sanctus Messor on 2007-09-27
They were integrated because he couldn't solve why Beryl would not run properly.

My Specs
[EVGA NVIDIA nForce 680i SLI ATX]("http://www.newegg.com/product/product.asp?item=N82E16813188013")
Core 2 Duo 6750 2.66GHz
4GB RAM
nVIDIA 8800 GTX
and 2 separate 500GB HDD (one runs Ubuntu, the other dual XP Vista)

---

### Post by PmDematagoda on 2007-09-27
You have a very good and new video card, which just requires you to download and install the latest Nvidia driver for Linux in the Nvidia website. There is absolutely no necessity for integration of the driver into the kernel itself.

P.S. After installing the Nvidia drivers, configure Xserver using:-

"sudo dpkg-reconfigure xserver-xorg"

After configuration just "startx"

---

### Post by madoracle on 2007-09-27
> **Sanctus Messor said:**
> They were integrated because he couldn't solve why Beryl would not run properly.

Ah, gotcha. I just nixed Beryl rather than use the drivers from NVidia. Still, to each their own. 

To the OP: Did you change anything right before this began happening? Also have you tried checking your X config?

---

### Post by PmDematagoda on 2007-09-27
> **madoracle said:**
> Ah, gotcha. I just nixed Beryl rather than use the drivers from NVidia. Still, to each their own. 

To the OP: Did you change anything right before this began happening? Also have you tried checking your X config?


Why do people still use beryl? Compiz-fusion is better than Beryl and Compiz as they fused together making.......Compiz-fusion.:)

---

### Post by Sanctus Messor on 2007-09-28
So ok, I have a 24" monitor, 1920x1200. Yes I can change the range if need be but one of the problems I ran into was the range. When I first installed Ubuntu from the Live Disc I had to set it to 1280x1024 (or what ever the max setting is) to boot the disc, after install it would boot but there would be no video output. So I removed the splash and that fixed the booting problem. Then came Beryl and the nVIDIA drivers. The drivers would download and would have to activate them from the restricted drivers. Every time I did so the Xserver crashed and I had to reconfig from the boot terminal. Then the nVIDIA drivers were no longer active and during the Xserver config if I chose NVIDIA it would not work. So I had to go with the Default. We intergrated the NVIDIA drivers and then everything worked fine. I got Guild Wars running under WINE and everything was good. So then we decided we would try the Beryl setup again, and this time it worked. I love the beryl effects (NEED to burn the windows I close) but if Compiz-Fusion has the same effects and/or is just over all better I would look into it. Anyway, If the NVIDIA drivers dont install properly a second time around, what should I do?

Long Story Short, What do you recommend I do? I have no problem with re-installing.

---

### Post by nowshining on 2007-09-28
what's ur video card?

---

### Post by Sanctus Messor on 2007-09-28
>  My Specs
[EVGA NVIDIA nForce 680i SLI ATX]("http://www.newegg.com/product/product.asp?item=N82E16813188013")
Core 2 Duo 6750 2.66GHz
4GB RAM
nVIDIA 8800 GTX
and 2 separate 500GB HDD (one runs Ubuntu, the other dual XP Vista)
[B]
nVIDIA 8800 GTX[/B]

---

### Post by nowshining on 2007-09-28
are the drivers still integrated into the kernel?

---

### Post by PmDematagoda on 2007-09-28
You need the latest drivers for Linux in the Nvidia wabsite in order to use the 8800 GTX VGA card. They can be found here:-

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by heldal on 2007-09-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Sanctus Messor said:**
> [B]
nVIDIA 8800 GTX[/B]

That explains a lot. The nvidia driver in Feisty is incomplete. A file that is required for the 8800GTS/GTX has been omitted in packaging. The solution is to either use nvidia's drivers outside of the packaging system, or to get hold of the missing file somewhere.

You said you had it working before. Would that be with nvidia's original drivers? If so you'd have compiled and linked a kernel module during installation. That module would have to match the kernel version and would have to be re-compiled if the kernel is changed. Did you by any chance install a new kernel lately, or maybe a kernel update via the software update system? If you did, and are using custom drivers, just boot into "recovery mode" from grub and repeat the installation steps for the nvidia driver. That'll give you a new kernel module compatible with your new kernel.

This illustrates problems that arise when people use kernel-components outside of the packaging system. Automatic updates may then cause this kind of inconsistencies and the users have to remember to reinstall any custom bits they've added as kernel modules are strictly tied to a certain version of the kernel. The most future-proof solution for this particular problem is to use the "nvidia-new" package in Feisty and manually add the missing file. That should give the packaging system the opportunity to fix the problem once a patch is released. Examine the attached bug-description for additional explanations and descriptions of the workaround.

---

### Post by nowshining on 2007-09-29
"boot into "recovery mode""

no no if using the nvidia drivers from the site - it  will complain about the run level - :P

---

