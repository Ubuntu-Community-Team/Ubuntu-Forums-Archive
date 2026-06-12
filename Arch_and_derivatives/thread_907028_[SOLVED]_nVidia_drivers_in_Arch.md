---
title: "[SOLVED] nVidia drivers in Arch"
date: 2008-09-01
forum: Arch and derivatives
---

### Post by erickghint on 2008-09-01
I just installed Arch for the first time, and before going any farther I'd like to install my video drivers. I'm a bit confused, however, as the Beginner's Guide states that the nVidia drivers are to be installed via pacman -S nvidia ... I need to use the beta drivers, since my card isn't supported as of yet (to my knowledge). Should I go about this in the normal

```
sh NVIDIA-Linux-x86-177.13-pgk1.run
```

and if so, which packages are needed for the install? I wasn't able to find much on the wiki, although admittedly I'm stupid tired at the moment. I know for Ubuntu I needed build-essential. Any help would be greatly appreciated.

---

### Post by crimesaucer on 2008-09-01
> **erickghint said:**
> I just installed Arch for the first time, and before going any farther I'd like to install my video drivers. I'm a bit confused, however, as the Beginner's Guide states that the nVidia drivers are to be installed via pacman -S nvidia ... I need to use the beta drivers, since my card isn't supported as of yet (to my knowledge). Should I go about this in the normal

```
sh NVIDIA-Linux-x86-177.13-pgk1.run
```

and if so, which packages are needed for the install? I wasn't able to find much on the wiki, although admittedly I'm stupid tired at the moment. I know for Ubuntu I needed build-essential. Any help would be greatly appreciated.


Which card do you have?


My card is the NVIDIA GeForce 7150M / nForce 630M and is on the supported card list for the regular nvidia driver which is 173.14 in Arch..... soon the driver in the Arch repository will be the 177.70 driver, which is beta right now..... and can also be used from either ABS or AUR.


What I did when I first installed was I installed these packages: xorg, xterm, nvidia, nvidia utils, and the nforce-utils (because I have nForce 630M).


Then, instead of running xorg -config, I ran:

```
nvidia-xconfig --composite

```


..... because I knew I would be using compositing. That made a perfect XF86Config that I'm still using with my new beta drivers. 


You can run this command to make sure that it worked: 

```
startx
``` 


Then finish your install and make any adjustment using the nvidia settings manager gui, or edit the /etc/X11/XF86Config file.


here is the wiki page for that: [http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)

---

### Post by mips on 2008-09-01
> **erickghint said:**
> I just installed Arch for the first time, and before going any farther I'd like to install my video drivers. I'm a bit confused, however, as the Beginner's Guide states that the nVidia drivers are to be installed via pacman -S nvidia ... I need to use the beta drivers, since my card isn't supported as of yet (to my knowledge). Should I go about this in the normal

```
sh NVIDIA-Linux-x86-177.13-pgk1.run
```and if so, which packages are needed for the install? I wasn't able to find much on the wiki, although admittedly I'm stupid tired at the moment.

Do you have Yaourt installed?
If not add these repos to your **/etc/pacman.conf**, [http://archlinux.fr/yaourt-en](http://archlinux.fr/yaourt-en)
Then do a **pacman -Sy yaourt**

NOTE: Run yaourt as normal user & not root for the instructions below.

Do a **yaourt -Ss nvidia** and it will give you a list of nividia drivers **including** those in AUR.

**yaourt -S nvidia-beta**  will install version 177.70-2
**yaourt -S nvidia-utils-beta** will install the corresponding utils version.

Simple as that.

---

### Post by erickghint on 2008-09-01
> Which card do you have?

I have a GTX260, which sadly has given me tons of headaches in Linux... :( I love the card, but wow I wish nVidia would hurry up and add better Linux support for their newer cards.

---

### Post by mips on 2008-09-01
> **erickghint said:**
> I have a GTX260, which sadly has given me tons of headaches in Linux... :( I love the card, but wow I wish nVidia would hurry up and add better Linux support for their newer cards.


Did you try installing the nvidia beta drivers as per my above post? Right after that post I tried it myself and the beta drivers work fine here although I have a different card to you.

---

### Post by erickghint on 2008-09-01
oh heh... not yet. The previous post was a reply to the question of which card I had :) It was a bit of a headache the first time I tried to install the drivers in Ubuntu. I'm about to try your method for Arch right now, I'll let you know how it turns out.

---

### Post by mips on 2008-09-01
> **erickghint said:**
> It was a bit of a headache the first time I tried to install the drivers in Ubuntu. I'm about to try your method for Arch right now, I'll let you know how it turns out.


I think you will be suprised how easy it is.

Just remember to follow these steps after you have installed the driver, [http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards](http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards)  obviously ignore the first step of installing the driver as you are doing it slightly differently.

---

### Post by crimesaucer on 2008-09-01
> **erickghint said:**
> I have a GTX260, which sadly has given me tons of headaches in Linux... :( I love the card, but wow I wish nVidia would hurry up and add better Linux support for their newer cards.


I'm sure that you already knew that your new card was supported: [ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/177.70/README/appendix-a.html)


Here is the nvidia forum for linux and the newset updates: [http://nvnews.net/vbulletin/showthread.php?t=118602](http://nvnews.net/vbulletin/showthread.php?t=118602)
 

@ mips- Does yaourt work in the tty console at the beginning of an install before you've installed xorg? 


If it does, I would follow those instructions when installing xorg and the new beta drivers for your very new nvidia... just do the same install instruction I said, using the yaourt app instead of pacman, and use the newer beta 177.70 packages instead of the ones in the Arch repository.


You could also use the AUR and makepkg to build the same beta packages, except using yaourt sounds easier for someone new to Arch..... I personally like using pacman and building all of my packages from AUR or ABS using the PKGBUILDS, but I've heard that the yaourt is a really good app for easily installing all of the packages and dependencies from the AUR and ABS and maintaining updates.

---

### Post by mips on 2008-09-01
> **crimesaucer said:**
> 
@ mips- Does yaourt work in the tty console at the beginning of an install before you've installed xorg? 


Yes it does.

As per my instructions you have to first enable the archlinux.fr repos and then sync repos and install yaourt with pacman. After that you can use yaourt to install from AUR (or the repos). Yaourt is one of the first things I install after I have rebooted into a fresh base install.

---

### Post by erickghint on 2008-09-01
Good god I've had a busy day... at any rate, at the end of everything, it gave me an error stating that I was missing fakeroot. I'm reading up on that as we speak, but it seems I may not even have time to do that. My kids are being little terrorists. I'm going to see how much I can get done before I'm called away, yet again.

---

### Post by erickghint on 2008-09-01
Ahh... After taking about 2 seconds to figure out the fakeroot thing, I installed it and went about my way. While installing the beta-utils I had an error... something about the mirror I had chosen being down. It took another 2 seconds to navigate over to the mirrors list and find another one. After that, it was all good. I really want to say thank you, both, for your replies. You've been nothing but helpful. Again, thanks a ton :)

---

