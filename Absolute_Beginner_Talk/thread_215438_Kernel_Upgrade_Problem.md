---
title: "Kernel Upgrade Problem"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-13
Since I installed Ubuntu several days ago, I'd been running on the 386 kernel. I was having problems with Ubuntu being a little slow and some programs constantly eating 100% of my CPU. Since I run an Intel Celeron processor, I was told to upgrade to the 686 kernel.

So I downloaded the required .debs and installed them.

Now here are my problems:

1. After rebooting with the 686 kernel, there is no noticable increase in speed, and the same CPU usage problems are present. In other words, the new kernel is apparently no better than the old one.

2. When I boot up, it now gives me the option to boot either the 386 or the 686 kernels. Am I supposed to uninstall the 386 kernel?

3. I'm not sure what to do now. I'm fairly certain I installed the kernel correctly, but if I did anything wrong, please let me know.

Any help would be really appreciated.

---

### Post by Hexx on 2006-07-14
Well, after searching around the forums it seems that not many people notice any change in speed when switching to the 686 kernel... :???:  I'm running an extremely old processor (500 MHz) so I guess I shouldn't have expected much.

I should also probably install the nVidia drivers, since I haven't done that yet, and my CPU usage problems are primarily when running graphics-heavy apps (like VLC and zSNES). Hopefully this will help solve the problem.

Also, it's now obvious why GRUB leaves the option for me to boot with the 386 kernel ;) 

However, if anyone has any advice, I'm listening!

---

### Post by trent dillman on 2006-07-14
Install sysv-rc-conf and do some research on each of the services before turning them off. This should help speed things up. Also, try a lightweight desktop environment like icewm, fvwm, or fluxbox (sorry, xfce users).

---

### Post by Hexx on 2006-07-14
> **trent dillman said:**
> Install sysv-rc-conf and do some research on each of the services before turning them off. This should help speed things up. Also, try a lightweight desktop environment like icewm, fvwm, or fluxbox (sorry, xfce users).

Yes, I've looked into turning off some services. I did that with WinXP and it really improved performance.

I know I probably should've gone with XUbuntu, but I really like GNOME :)

---

### Post by trent dillman on 2006-07-14
try running icewm or fluxbox with some gnome services running (like gnome-volume-manager).

---

