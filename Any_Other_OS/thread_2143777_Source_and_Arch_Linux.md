---
title: "Source and Arch Linux"
date: 2013-05-10
forum: Any Other OS
---

### Post by Rukiri on 2013-05-10
I'm moving away from source distros but there are some things I still need to compile, arch linux is somewhat of a hybrid distro it's binary by default but does have a ports system so it can compile from source.

I've also been spoiled by gentoo by adding options I don't need in a package and that's because of USE Flags, now since arch can compile it can also remove or add options to the package but you have to manually do it by commenting out options you don't need like theora for vlc for example.  or a52dec (who uses this? it doesn't compile in arch anyway though).

I'm aware of tools like abs and pacbuilder, I have heard of srcpac but it looks like it's 2 years old without any development, same with pacbuilder.  
Is there any src tools for arch other than these?

---

### Post by trent.josephsen on 2013-05-10
Assuming the ./configure script (or equivalent) recognizes the flag "foo", wouldn't
```
USE=foo makepkg
```
do the trick?

---

### Post by mips on 2013-05-10
These a global config file where you can specify USE Flags etc from what I remember.

---

### Post by Rukiri on 2013-05-12
I've never heard of a global config file for such use flags, I think you just need to edit the configure section of the PKGBUILD and just do --enable-something command.  It's how I enabled dts and removed theora from my vlc build.

---

### Post by mips on 2013-05-13
> **Rukiri said:**
> I've never heard of a global config file for such use flags,...

[https://wiki.archlinux.org/index.php/Makepkg](https://wiki.archlinux.org/index.php/Makepkg)

---

### Post by Rukiri on 2013-05-13
> **mips said:**
> [https://wiki.archlinux.org/index.php/Makepkg](https://wiki.archlinux.org/index.php/Makepkg)
Still no use flags but I think with arch you have to manually go through the configure section, with gentoo the use flags are variables for that section of the build.

That's just a file for changing your cflags, which is pretty much all you need to do with arch.

---

### Post by trent.josephsen on 2013-05-13
Not sure what I was thinking earlier, of course a configure script won't observe Gentoo's meaning of USE.

Nothing prevents you installing Portage on Arch, though why you'd want to ruin a perfectly good Arch installation with half of Gentoo is anyone's guess. The "big" advantage of custom compilation is being able to specify -march; enabling and disabling tiny components is far more nitpicky than I'm willing to put up with for no measurable benefit. That's one reason I left Gentoo several years ago. But whatever.

---

### Post by Rukiri on 2013-05-14
> **trent.josephsen said:**
> Not sure what I was thinking earlier, of course a configure script won't observe Gentoo's meaning of USE.

Nothing prevents you installing Portage on Arch, though why you'd want to ruin a perfectly good Arch installation with half of Gentoo is anyone's guess. The "big" advantage of custom compilation is being able to specify -march; enabling and disabling tiny components is far more nitpicky than I'm willing to put up with for no measurable benefit. That's one reason I left Gentoo several years ago. But whatever.
You're absolutely right,  I have a custom compiled KDE 4.10.3 setup on Gentoo and the just compiled from KDE's official sources on my linux from scratch box (the box I test everything new on before I do it on my main system) and I found really no difference in speed, boot (basically typing startx until you're at your desktop) was roughly the same, LFS booted a bit quicker though...   

Now I have no time to do a LFS on my main system, it took several days to finish it on my test system (I could just copy it to disk to an SSD and rerun grub install and than run a script to recompile the system with my cflags)...   I was looking at Crux linux for this very reason, it uses BSD style init scripts, arch USED to! and it has a quick install, the install is binary so you do have to more than likely rerun a system compilation script similar to what source mage has, source mage would have been great if it were actually up to date.. GCC is behind, kde is behind, gnome is very behind..  well crux still has gnome 2, gnome 3 never hit the repos.. (I can fix that). 

USE Flags are very useless in the decade I did run Gentoo and compared it to my LFS box over the years, the USe Flag concept basically came from the package option screen when you install a package in FreeBSD(I don't know the actual name used, I just call it the Option Screen where it's a ncruses based menu).  Still, BSD-Ports is far superior, heck I'm even liking Crux's port system over Gentoos as it's simple.

Crux to me just seems like a source version of Arch just without the super bleeding edge packages.. The IRC channel seems active to, gentoo is too active where it's impossible to get your answer answered because people just fly in and I had to ask 20 times just so someone could catch it and answer it.  Crux is active just not super active and I find that a good thing, arch is super active but people answer right away.

Also Gentoo is BLOATED, yes I'm aware source distrobutions use a bit more space as they save the source but compared to LFS and gentoo it's night and day (several GBs of a difference)  on my test system I have a 6 512GB SSDs run in raid 10 and the same on my Gentoo box, when I finished my LFS install it used about 2.8GB of space of roughly 3TB of available disk space, Gentoo used about double that.  I know Stage3 makes it easier to install but it also bloats the system with features you just don't need and even crux on my system only used 2GB of 1TB of disk space and recompiled it was still 2.5GB so Gentoo is a bloated system from installation and it eats disk space for dinner... Other source distos don't do this, gentoo was a better distro when it offered stage 1 installs!

---

