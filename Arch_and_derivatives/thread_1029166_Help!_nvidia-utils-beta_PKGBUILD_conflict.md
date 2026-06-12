---
title: "Help! nvidia-utils-beta PKGBUILD conflict?"
date: 2009-01-03
forum: Arch and derivatives
---

### Post by mips on 2009-01-03
[http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=](http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=)

Can someone please tell me which item(s) or line(s) in the PKGBUILD I must comment out in order to avoid the libgl conflict I'm experiencing. Please provide the line# and quote the text. See AUR comments. The stupid thing insists on installing libgl as a dependancy and then after it builds it conflicts with libgl.

PKGBUILD here, [http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD](http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD)

---

### Post by handy on 2009-01-03
> **mips said:**
> [http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=](http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=)

Can someone please tell me which line in the PKGBUILD I must comment out in order to avoid the libgl conflict I'm experiencing. Please provide the line# and quote the text. See AUR comments. The stupid thing insists on installing libgl as a dependancy and then after it builds it conflicts with libgl.

PKGBUILD here, [http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD](http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD)

I don't know mips, I think you should probably move over to Redhat.

***[Edit:]** We'll miss you though. ;-)*

---

### Post by mips on 2009-01-03
> **handy said:**
> I don't know mips, I think you should probably move over to Redhat.


I'm a sucker for punishment so was thinking Gentoo, LFS or something in that line ;)

---

### Post by handy on 2009-01-03
> **mips said:**
> I'm a sucker for punishment so was thinking Gentoo, LFS or something in that line ;)

:lolflag:

Not Arch?  :confused:

---

### Post by mips on 2009-01-03
> **handy said:**
> :lolflag:

Not Arch?  :confused:

This has to date been the hardest frigging Arch install I have done (rephrase that to "trying to do"). Nothing wants to go right here. Maybe I should just boot into WinXP and play counter strike source instead...

---

### Post by handy on 2009-01-03
I have a pile of questions to ask on the subject, but instead, rather than ask the obvious I'll let you do what you have to, & ask you to let me know how it turned out in the end?

---

### Post by fwojciec on 2009-01-03
> **mips said:**
> [http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=](http://aur.archlinux.org/packages.php?ID=19224&O=&L=&C=&K=&SB=&SO=&PP=&do_Orphans=&SeB=)

Can someone please tell me which item(s) or line(s) in the PKGBUILD I must comment out in order to avoid the libgl conflict I'm experiencing. Please provide the line# and quote the text. See AUR comments. The stupid thing insists on installing libgl as a dependancy and then after it builds it conflicts with libgl.

PKGBUILD here, [http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD](http://aur.archlinux.org/packages/nvidia-utils-beta/nvidia-utils-beta/PKGBUILD)

I don't use the nvidia-beta package from AUR, I just build nvidia drivers by editing original PKGBUILD from extra -- but the problem in your case is completely banal, I think.  adamruss gave a good explanation in the AUR comments.  The problem is that pacman -U works a bit differently than pacman -S and will not automatically remove conflicting packages so you'll have to manually remove libgl (pacman -Rd libgl) after building the package and prior to installing it with pacman -U.

---

### Post by mips on 2009-01-03
> **fwojciec said:**
> I don't use the nvidia-beta package from AUR, I just build nvidia drivers by editing original PKGBUILD from extra -- but the problem in your case is completely banal, I think.  adamruss gave a good explanation in the AUR comments.  The problem is that pacman -U works a bit differently than pacman -S and will not automatically remove conflicting packages so you'll have to manually remove libgl (pacman -Rd libgl) after building the package and prior to installing it with pacman -U.

Thanks, but my question still stands. If I'm using yaourt and I need to edit the pkgbuild what would I edit. I'm referring to the comments before mine. People were editing the pkgbuild to make it work. 180.11 installed fine with yaourt, not so for 180.18-1

---

### Post by mips on 2009-01-03
I'm reinstalling. Building a package manually or with yaourt should not give me this much grief, it never has before.

Will keep you posted.

---

### Post by crimesaucer on 2009-01-03
I just built that same AUR package using pacman instead of pacbuilder. 


What I had to do (because of conflicting files), was I removed the previous 177.82 nvidia-utils with pacman -Rd to ignore dependancies. 


Then I had to force install the new AUR nvidia-beta-utils with pacman -Uf to overwrite the existing files.


Then I installed the official NVIDIA-180.18 beta from their FTP download page: [http://nvnews.net/vbulletin/showthread.php?t=122606](http://nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by santaslittlehelper on 2009-01-03
I just upgraded from 180.16 to 180.18-1

yaourt -Rd nvidia-utils-beta nvidia-beta
yaourt -Sy nvidia-utils-beta nvidia-beta

Without any trouble or edit of pkgbuild needed.
I know that don't answer your question, but maybe the issue is not the pkgbuild?

---

### Post by mips on 2009-01-03
Houston, we have liftoff!

Seing I only had a base install + xorg,alsa-utils,xfce I decided to uninstall all the stuff additional to base. When I reinstalled xorg from cache I noticed it was pulling in more files than what was in cache off the net which confused me.

So I simply purged all the stuff additional to base from my cache and reinstalled them, was not much.

I then removed libgl and built the nvidia-utils-beta & nvidia-beta packages manually and this time they built & installed fine. Mucked around with my xorg.conf a bit disabling hotplugging and voila I can start xfce with .xinit :)

I dunno what gremlim caused this but I'm just delighted I can get X up.

Startx however does not work, need to investigate that...

---

### Post by mips on 2009-01-03
> **santaslittlehelper said:**
> I just upgraded from 180.16 to 180.18-1

Without any trouble or edit of pkgbuild needed.
I know that don't answer your question, but maybe the issue is not the pkgbuild?

I could not install them on a fresh install of Arch. Some gremlin must have crept in somewhere. See my post above.

---

