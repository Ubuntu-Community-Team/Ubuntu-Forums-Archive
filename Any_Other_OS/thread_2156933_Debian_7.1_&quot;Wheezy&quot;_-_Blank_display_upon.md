---
title: "Debian 7.1 &quot;Wheezy&quot; - Blank display upon boot"
date: 2013-06-23
forum: Any Other OS
---

### Post by [::AP::] on 2013-06-23
Hello all,

In the past, I had Debian 6 "Squeeze" running flawlessly on this laptop. The laptop is a Dell Inspiron E1405. I'll post specs if needed, but I don't want to clutter this post.
This weekend, I decided to upgrade to Debian 7 "Wheezy" via a fresh install. 
I've reformated all partitions (/, /usr, /var, /tmp) except for /home (and swap I guess doesn't need to be reformatted upon resinstallation). I can provide partition details if needed, but my guess is that it is irrelevant. 

Once fully installed, everything seems fine. GRUB, then Debian begins booting, and I can see the verbose boot in large font (before it adjusts to laptop resolution). As soon as the verbose boot output adjusts to the laptop screen resolution, the screen goes blank. The laptop remains on, but I cannot see the CLI login (no GUI installed).

It appears that I can blindly enter commands. So far the only thing I've done is logged in as root and then rebooted.
I've done two net installs via USB and one "DVD 1" install via USB. I checked the MD5 for the DVD 1 iso. Everything was fine.

This problem did **not** occur with *every* boot when installed with the Net install. Only about 25% of the time was I able to see the basic CLI after boot. 
[s]I have not been able to get Debian to boot correctly with the latest DVD 1 install.[/s] Nevermind just got it, but alas, the problem is still prevalent. 

I've only encountered this issue when I installed Arch (boy...that was an adventure...) last year on this laptop. My previous Ubuntu 9.10 through 10.10 installs worked fine, as well as the Debian 6 install.
It seems like there will be a relatively easy fix, but I'm not sure where to begin. 

[s]I'll post a video of the boot when I get the chance. Apparently YouTube just introduced slow-mo video uploads...I'll give that a shot...[/s] *Nah I don't think it is needed at this point, unless someone asks specifically to see the output...*

Thanks!

---

### Post by buzzingrobot on 2013-06-23
Can you switch to a console and log in via alt-f2, alt-f3, etc. ? If so, enter "startx" and take a look at the (error) messages it emits.

---

### Post by [::AP::] on 2013-06-23
> **buzzingrobot said:**
> Can you switch to a console and log in via alt-f2, alt-f3, etc. ? If so, enter "startx" and take a look at the (error) messages it emits.

Switching to other tty's does nothing.

And X isn't installed. I did not install a desktop environment during the install process. I might install X + XFCE4, and also possibly see what happens when lightdm is thrown into the mix.

---

### Post by buzzingrobot on 2013-06-23
Tried "nomodeset"?  My Nvidia card often requires it else it boots into blackness with certain versions of Nouveau and 3.2/3.3 kernels.

---

### Post by [::AP::] on 2013-06-24
> **buzzingrobot said:**
> Tried "nomodeset"?  My Nvidia card often requires it else it boots into blackness with certain versions of Nouveau and 3.2/3.3 kernels.

I'll give it a shot, but there is no graphics card in this laptop. 

I was thinking it is either a kernel issue or the lack of a display manager .

---

### Post by [::AP::] on 2013-06-24
> **buzzingrobot said:**
> Tried "nomodeset"?  My Nvidia card often requires it else it boots into blackness with certain versions of Nouveau and 3.2/3.3 kernels.

No change. 

I used the method here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I may try installing the latest Crunchbang, which is based on Debian.

---

### Post by [::AP::] on 2013-06-24
Crunchbang works. Not exactly what I wanted, but I guess it works*. 

I won't be marking this as [SOLVED] because a true solution was never found. 

*I'll be using this laptop as a personal ownCloud server, and possibly as a small Minecraft server (as was the laptop's use when on Debian 6 Squeeze).
Really any distribution can work as a server, I was just going towards Debian (without a GUI) because it was stable and lightweight (or so I think?)
If anyone can see issues with using Crunchbang (without X running) as a small file server, let me know. Other suggestions are welcome, but I'd like to stay in the Debian world...

Thanks, for now. Although I'd still like to figure out why Debian 7 Wheezy was not working. Any input is welcome.

---

### Post by buzzingrobot on 2013-06-24
The Crunchbang community is friendly and smart.  If a thin layer over Wheezy like Crunchbang works on hardware that Wheezy doesn't, they can help you figure out why.

---

### Post by [::AP::] on 2013-06-24
> **buzzingrobot said:**
> The Crunchbang community is friendly and smart.  If a thin layer over Wheezy like Crunchbang works on hardware that Wheezy doesn't, they can help you figure out why.

Yeah :)

This forum has mainly Ubuntu know how-ers. 
I should head on over to the respective distro forums. 

Thought it would be a general quick fix, hence why I posted here, if an explination is needed.

But thanks for your help, I appreciate it.

---

