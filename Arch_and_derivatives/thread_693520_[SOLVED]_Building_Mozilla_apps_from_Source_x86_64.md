---
title: "[SOLVED] Building Mozilla apps from Source x86_64"
date: 2008-02-11
forum: Arch and derivatives
---

### Post by bwtranch on 2008-02-11
Anybody have any experience building from source with Mozilla? Seems like every time I try one, like a beta firefox, I get just about there and get distracted (bored, cat's cryin', baby's barkin', etc) and after all my current app works anyway, so why bother. Like yesterday, I was going to try it again on Composer, same ole dependency list, couldn't find one and then found nvu in the repos. I kinda look at it as a challenge not yet fulfilled, but maybe it's not worth it. It's like backing up a DVD, I don't have to, I just want to see if I can. Plus with these media corporations, it's like a carrot and a stick! Besides, I have stock in a lot of these companies and I don't think they are going to go broke by letting average people backup their stuff. Real pirates break it down bit by bit anyway and it leaves the encryption intact. So what really is the point? Control.
This thing has been going on forever. I remember (showing my age) when recordable cassette tapes were delayed by a few years over this issue. Now, nobody cares if you make a copy of a cassette, nobody hardly uses them anymore anyway. Did it hurt the music industry, of course not. It's larger and more diverse than ever. Well, anyhow, I kinda went off on a tangent, but not that far off, because it does relate to the original topic. Any thoughts?

---

### Post by fwojciec on 2008-02-11
There should be a beta firefox PKGBUILD in AUR -- which should make building from source easy:

firefox3 beta: [http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)
nvu: [http://aur.archlinux.org/packages.php?do_Details=1&ID=9407&O=0&L=0&C=0&K=nvu&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=9407&O=0&L=0&C=0&K=nvu&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)
Have a look in AUR -- there are alternative version for each available.

Personally I alaways recompile Firefox from source -- one of the few apps that actually benefit from being recompiled manually, IMO.  I just get the PKGBUILD from the ABS tree (see the wiki if you haven't tried ABS yet) and make a few changes to the PKGBUILD and mozconfig file (to enable branding and xinerama support) and then build it using makepkg.

---

### Post by bwtranch on 2008-02-11
> **fwojciec said:**
> There should be a beta firefox PKGBUILD in AUR -- which should make building from source easy:

firefox3 beta: [http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=14351&O=0&L=0&C=0&K=firefox3&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)
nvu: [http://aur.archlinux.org/packages.php?do_Details=1&ID=9407&O=0&L=0&C=0&K=nvu&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=9407&O=0&L=0&C=0&K=nvu&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)
Have a look in AUR -- there are alternative version for each available.

Personally I alaways recompile Firefox from source -- one of the few apps that actually benefit from being recompiled manually, IMO.  I just get the PKGBUILD from the ABS tree (see the wiki if you haven't tried ABS yet) and make a few changes to the PKGBUILD and mozconfig file (to enable branding and xinerama support) and then build it using makepkg.
Thanks fwo, I have been doing some reading about the ABS and AUR and I haven't quite got it down yet. Just need a little more practice and it seems I'm reading two different wikis that differ in the hierarchy of the directories. i.e. Where to put the files. Need to establish my system on my nice clean install and not get too messy (like some dirty windows:)) I wound up doing it the usual way, though. I even tried to get build-essential, didn't work, of course. Say, that brings up another question. Would it be a bad idea to enable some Ubuntu repositories?

---

### Post by fwojciec on 2008-02-11
> **bwtranch said:**
> Thanks fwo, I have been doing some reading about the ABS and AUR and I haven't quite got it down yet. Just need a little more practice and it seems I'm reading two different wikis that differ in the hierarchy of the directories. i.e. Where to put the files. Need to establish my system on my nice clean install and not get too messy (like some dirty windows:)) I wound up doing it the usual way, though. I even tried to get build-essential, didn't work, of course. Say, that brings up another question. Would it be a bad idea to enable some Ubuntu repositories?

AUR/ABS/makepkg are the coolest tools in Arch and it definitely pays to learn to use them.  Makepkg is much better than compiling manually because it'll take care of resolving dependencies for you, and will compile things into a package that can be later placed in the local repo and removed, reinstalled, updated, and otherwise managed with pacman (it becomes cleanly and elegantly integrated into your system, in other words).

As for using Ubuntu repos -- it's not going to work, I'm affraid.  AUR should have everything you need, and if it doesn't have something you can always request that someone packages what you need for you (or you can package it yourself and provide it for the community at large).

---

### Post by santaslittlehelper on 2008-02-12
Hi

I think base-devel equal build-essential.
pacman -Ss | grep base-devel

If you are referring to a change in the wiki recently then I noticed it too, I am still learning myself, but if you go through that one ABS page in the wiki I think you'll get the basics down quickly.

---

### Post by bwtranch on 2008-02-12
Thanks santa :). That is the one. Checked it out and I do have everything. I did some installs with ABS last night and have it down. Looks like I'm all checked out and ready to fly. Gee, that was easy and only took really a few hours, for the whole thing. I'll mark this one as solved. BTW firefox3 looks really good. Tastes great (more filling, though).

---

