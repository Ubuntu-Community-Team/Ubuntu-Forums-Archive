---
title: "absolute newbie needs help"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by windowsatemyhomework on 2005-09-11
I have finally gotten sick of windows and installed k/ubuntu (both gnome and KDE - I think I'll be using KDE more) on my second HDD. I'll get off of windows entirely once I get everything configured to my liking. In the meantime, there are a few hurdles to getting that done. Help with all of these, or help with any one, would be greatly appreciated.

1. The maximum screen resolution that either gnome or KDE will allow is 1024X768. My flat screen and I disagree with this, we would like 1280X1024, but I can't figure out how to make it happen. I suspect that a solution would come with a proper installation of the drivers to my BFG GeForce 6800 PCIe, but I haven't been able to accomplish that.

2. My logitech MX1000 mouse works, but none of the extra buttons (besides basic up/down scrolling) work. That would be cool, even moreso if the extra buttons were customizable like with logitech's windows drivers. While we're at it, there are extra media buttons on my keyboard (also logitech) that don't work.

3. I have no sound coming out of my Creative Audigy 4 Pro card. With the money I spent on that thing, this is a MUST.

4. I have a TV tuner card, a WinFast PVR 150 w/remote control. I think I would migrate without it (because I have a suspicion that it won't port to linux), but if there is a solution, I want to know about it!

5. This is not necessary if I abandon windows entirely, but would be helpful even if I am.

6. I have downloaded and tried to install the flash and shockwave plugins for konqueror in KDE and firefox in gnome, but have been unable. I have installed those firefox plugins in windows before, but it won't work here. I also read somewhere that the shockwave and flash plugins aren't working on AMD64 architecture. Is there a workaround?

7. I have an sli motherboard, and a second BFG 6800 PCIe on the way. Will they work "right out of the box", or will some extra configuration be necessary, and if so, what?

I know that this is a lot, and I think perhaps that there might be enough things that didn't happen correctly "right out of the box" to justify trying a different distro. Let me know what you think. If you have any answers, I would be extremely grateful. Thanks!

---

### Post by mustang on 2005-09-11
2. Might want give the following two a go. I only needed the latter HOWTO

[http://www.ubuntuforums.org/showthread.php?t=3828](http://www.ubuntuforums.org/showthread.php?t=3828)
[http://www.ubuntuforums.org/showthread.php?t=28374](http://www.ubuntuforums.org/showthread.php?t=28374)

Keyboard (i'm in the same boat)
[http://www.ubuntuforums.org/showthread.php?t=27039&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27039&page=1&pp=10)

---

### Post by aysiu on 2005-09-11
As I was reading your message, my first response was going to be a link to how to fix your screen resolution (it's an easy fix--believe me), but then I read about all the other problems you're encountering.

Look, you can stick it out with Ubuntu if you want, and I think if you do stick it out, you'll be rewarded, but honestly... if there are that many things wrong from the start, you may be better off with another distro (I'd recommend trying out Mepis or Blag... maybe SuSE).

Hardware detection should be one of the major factors in choosing a distro. If it detects everything but one thing, that should be fine. Three or more... ugh.

---

### Post by matthew on 2005-09-11
I've gotta agree with aysiu here. That is a lot of stuff to fix. I think it could be done, but there is probably an easier way. As much as I like Ubuntu, I would also say that it is not in competition with other Linux distros and no one here would feel bad if a different distro ended up working better for you. On the other hand, if you decide you want to stay here (because the community is one of the best around) you can ask for help on the problems and it is likely that most if not all of them will be fixed.

---

### Post by windowsatemyhomework on 2005-09-11
I would prefer to stick it out with k/ubuntu. This support community is unmatched as far as I have seen, and since I am new to Linux entirely, that is worth quite a lot. I also choose to see the configuration issues as an opportunity to "pop the hood" on linux and start to learn what I'm doing early on.

Besides which, my long list is a little misleading. I made a mistake with the numbers, so there's 6, not 7. Three of those 6 (TV, SLI, flash plugin) would probably be issues with any distro. That leaves the resolution, which is an easy fix, the mouse, which I have made progress on from the many howtos out there (and have learned a lot in the process), and the sound, which can't be too difficult.

I may very well end up throwing up my hands and moving on, but I haven't yet given this an effort that would match the benefits of using a distro with this kind of support community.

In the meantime, there is a significant gap in my knowledge that would make parts of this a lot easier. I have found debian packages that provide significant parts of the mouse puzzle, but don't know how to install them. The debian packages open in ark, and I find a debian binary that has only the text 2.0 in it, and two or more .tar.gz files, which also open in ark. I think I should be using synaptic/kynaptic, but I don't know how.

---

### Post by matthew on 2005-09-11
Cool. We are glad to have you around. First task: help you learn the basics. I'll answer the "how to install debs" in just a second. Let me also suggest you read the links in my signature, they will help you a lot. Then, begin by asking your questions one at a time, each in new threads with really clear titles. That way people will see the subject and those who know something about the topic will be likely to take a look and help quickly.

The easiest way to install a deb is by using the terminal. Here's a step by step. Before you try it with the debs you downloaded, read the following disclaimer--if you want to install a deb be aware that if it was not made specifically for the Ubuntu distribution it could cause you some problems, not just with installation but with other software that is already installed on your computer. The only way to be sure you don't break your system (or just do something requiring some frustration while trying to fix it) is to install using apt-get/aptitude/synaptic from the current release repositories. Right now, that means using the Hoary repos. The other option is to learn to download source code and compile it on your computer.

Now that you have been properly warned, I'll tell you that this kind of breakage is not a guarantee and the debs you downloaded may work to help you fix your mouse...but they may not, so before you try to install them you may want to post a new thread about the problem and see if there is a better solution.

Okay, enough with that. Here's how to install a deb:
1) open a terminal
2) cd to the directory where the deb was downloaded
3) type this: sudo dpkg -i <package name>.deb
4) enter your password
5) wait for it to finish and you are set

The installed package will also appear in synaptic so you can uninstall it from there easily until you learn the command line method (assuming you want to, not everyone does and that's really okay).

Have a great day and welcome aboard! I hope we can get everything up and running for you quickly and without it being a hassle.

---

