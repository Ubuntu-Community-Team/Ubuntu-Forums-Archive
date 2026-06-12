---
title: "graphics switching on macbook pro 8,2"
date: 2012-11-19
forum: Apple Hardware Users
---

### Post by sunpho on 2012-11-19
Hi Macbook users, it's a couple of weeks that I am trying to make Ubuntu works with integrated graphics card on my Mac Book Pro 8.2, with little success. The best I managed to do has been to install efi grub 2 and ubuntu 12.10 (amd64+mac) but no way I manged to start X with neither of the two graphics card. Before entering into details on my efforts I would prefer to listen to comments and general suggestions on how to make a clean installation able to perform graphics switching between AMD and intel card.

Since most of the documentation available (such as [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)) a bit outdated, I have questions for people that managed to make graphics switching work recently, in particular:

1) is the 12.10 amd64+mac distribution the correct point where to start for this work? otherwise, which is the most appropriate one?
2) is 3.5 kernel included in the distribution already implementing all the patches, or does it need to be recompiled including patches?
3) is it still necessary to pass parameters (such as i915.modeset=1) to the kernel?
4) are the tricky "outb" parameters to be still passed from grub?
5) are there modules that need to be blacklisted?

What's your experience? Thanks in advance for any help!

---

### Post by Nothung on 2013-02-15
This thread is a few months old, but I'm going to bump it since it covers exactly where someone ends up when they try to get Quantal running on a MacBookPro 8,2 with EFI.

The only thing I've managed to get working is the integrated graphics, using the old GRUB outb trick to write to the gmux device.  You can do this by hitting **e** in the GRUB boot menu and appending these four lines to the end of the buffer:

```
outb 0x728 1 # Switch select
outb 0x710 2 # Switch display
outb 0x740 2 # Switch DDC
outb 0x750 0 # Power down discrete graphics
```

You can make this permanent (at least until the next kernel upgrade) by adding it to /etc/grub/grub.cfg .  


Of course this is only a band-aid solution so that you can at least get X running.  It completely turns off the discrete graphics, so that it doesn't even show up in lspci.

What I've figured out so far is that:
[LIST=1]
[*]You need to install the Catalyst driver from the ATI website, as the one bundled with Ubuntu may not deal properly with hybrid graphics.
[*]It is possible that only a specific version of the drivers will work with hybrid graphics.
[*]Even then, there is a bug in the intel drivers (xserver-xorg-video-intel) when using hybrid graphics: "undefined symbol: noXFree86DRIExtension".  There is a patch available, along with a PPA: [https://launchpad.net/~andrikos/+archive/ppa](https://launchpad.net/~andrikos/+archive/ppa)
[*]The latest version of this PPA causes an X server segfault on my machine, so you might have to hunt down that patch and build the package yourself.
[*]Even then, something goes wrong with X.  I'll update this post when I figure out what it is.
[/LIST]

I had a bunch of links to back these up, but I seem to have lost some of my notes from when I did this back in November. (I wish I had seen your thread then!)

---

### Post by Chav on 2013-02-16
[http://ubuntuforums.org/showthread.php?t=2103743](http://ubuntuforums.org/showthread.php?t=2103743)

---

