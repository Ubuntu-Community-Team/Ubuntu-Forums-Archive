---
title: "[SOLVED] System Restore"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by reeksy on 2008-02-20
Hi

I've been using Ubuntu for a few weeks now, and it's great! Problem is; I think I’ve messed up some root drivers somewhere. I was playing about with trying to get my NVIDIA graphics card to work and I installed/uninstalled something I shouldn’t have within the package manager. 

Since then I’m stuck without any internet connection or sound! Also the maximum resolution I can run is 800x600! It seems that somewhere something pretty serious has gone wrong!

**So, my question is:** Is it possible to restore to entry level settings/drivers without losing all my data?

I thought it might be possible to do via the live CD, so I popped it in and had a look through the options, but nothing seemed obvious. Any help on this would be great

Kind Regards
Jon

---

### Post by seventhc on 2008-02-20
As far as a know, there is no system restore feature yet.
But someone here can probably help you get back in shape. :)

---

### Post by reeksy on 2008-02-20
I'm hoping that I can copy come core files/folders from the live CD over to my hard disk, but I need some help knowing which!

If I can't, and I need to do a complete re-install then fair enough. But if it comes to that (and this might be the wrong place to ask) but does anyone know a flavor of Linux that works well with NVIDIA drivers? As I’ve been having real trouble with Ubuntu.

Regards

---

### Post by seventhc on 2008-02-20
you'll be able to copy from the live cd. Boot from the cd then once booted open a terminal and type
```

gksudo nautilus
```
Then you should be able to save data to a usb thumb drive. Not sure if you can burn a cd if you only have on cd drive as it will be in use for the live cd.
As far as what you need to save all depends on your needs. I don't copy the .Themes folder or anything, I have the 4 .tar.gz files for that. I usually just keep my .gnupg .ssh conky and mutt stuff. So really it's an individual choice.
I have my entire home folder on a dvd minus some videos that wouldn't fit. But I don't restore the entire folder, I just have it in case I have a need for it.
The ones I use I save to a usb thumb drive so I don't have to dig through the DVD.
I'm not sure what would be the best distro for you, but maybe someone here will have a better idea on that.

---

