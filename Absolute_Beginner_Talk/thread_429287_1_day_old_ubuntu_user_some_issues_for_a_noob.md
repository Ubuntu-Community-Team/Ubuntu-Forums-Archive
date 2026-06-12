---
title: "1 day old ubuntu user: some issues for a noob"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by [ITA]ArgH on 2007-05-01
hi guys! i'm a very beginner with ubuntu 7.04 (and linux too)... I installed yesterday ubuntu on my laptop...

I had some issues and problems that with some help i could resolve...

But now i still got some issues that i really can't handle:

- Sounds have a worse quality than windows, the wheel i used to set volume is no longer supported and if i set volume (internal speaker, wich it seems to be the master one) i heard a terrible and persistent scratch when no sound is playing, here's my sound card, it should be from realtek  ```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

- can't go suspend! using it will freeze my laptop and i have to manually turn it off with the keyboard shutdown button

- i still got my windows partition, and i'm using ntfs-3g to handle file there... I wonder if it is possible to have firefox in ubuntu  loading the same config, bookmarks, and plugin of the windows one. (with amule i could load the emule temp file) 

- Fonts look now different... In web pages i usually surf fonts are now completely different! Do i need a font package?

- Really a noob for linux so here's a noob question: in windozz there's a huge amount of useless thing especially services loaded into your system, they just turn down your speed... I'm asking myself if there's something useless to switch off in ubuntu to gain some speed

Anyway after two days on ubuntu, i 'm asking myself why i waited so long to move to linux... Hey it's soooo user friendly!! And i really like the package feature!!

---

### Post by jiminycricket on 2007-05-01
You can install the package named msttcorefonts if you want Windows-like fonts, and there are several howtos on here to get the rendering exactly like Windows.  But, usually I just set hinting to "none" in Gnome Font Preferences, and it looks as nice or better than Mac OS X fonts.

Suspend- do you have any proprietary (ati fglrx, nvidia) drivers installed?  What brand and model number of laptop?

Sharing Firefox profiles is a bit of a hassle between Linux and Windows, but there are several howtos for it on google (for Thunderbird, too).  Personally, I just use Google Browser Sync extension to keep everything sync'd up.

Ubuntu doesn't really have unnecessary services that I can think of.

---

### Post by [ITA]ArgH on 2007-05-01
thanks, 
yeah you're right i got an nvidia geforce go 6800 on my amilo fujitsu siemens, and it has those drivers... So i cant suspend with them?

---

### Post by ubnewbie2 on 2007-05-01
> **'[ITA]ArgH said:**
> hi guys! i'm a very beginner with ubuntu 7.04 (and linux too)... I installed yesterday ubuntu on my laptop...

I had some issues and problems that with some help i could resolve...

But now i still got some issues that i really can't handle:

- Sounds have a worse quality than windows, the wheel i used to set volume is no longer supported and if i set volume (internal speaker, wich it seems to be the master one) i heard a terrible and persistent scratch when no sound is playing, here's my sound card, it should be from realtek  ```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
```

- can't go suspend! using it will freeze my laptop and i have to manually turn it off with the keyboard shutdown button

- i still got my windows partition, and i'm using ntfs-3g to handle file there... I wonder if it is possible to have firefox in ubuntu  loading the same config, bookmarks, and plugin of the windows one. (with amule i could load the emule temp file) 

- Fonts look now different... In web pages i usually surf fonts are now completely different! Do i need a font package?

- Really a noob for linux so here's a noob question: in windozz there's a huge amount of useless thing especially services loaded into your system, they just turn down your speed... I'm asking myself if there's something useless to switch off in ubuntu to gain some speed

Anyway after two days on ubuntu, i 'm asking myself why i waited so long to move to linux... Hey it's soooo user friendly!! And i really like the package feature!!

I noticed that unbuntu (feisty) had my sound turned up very loud by default when I first installed.  This caused 'scratchy' sounds from my speakers, because it made all the electrical interference from my computer audible.  Having the sound up loud can also cause distortion, even if it doesn't sound overly loud, because one of the sources can be turned up high, but the master is turned down low. On some sound cards, this can cause distortion, until you lower the source volume, and raise the master a bit. Play with the mixer controls and see if you can improve it.

I don't know about all of Firefox's config, I didn't bother, but the bookmarks are easy to bring across.  Just open up the bookmarks menu, go to 'Organize bookmarks' and use File > Import .  Point it at the bookmarks.html file in you other Firefox profile directory and it will load them all.

Fonts are something I had trouble getting right, and some people like them set different to others.  Use the system font preferences to play around with smoothing settings and fonts until gnome looks good, then start Firefox and change the fonts there until you are happy. I have settled on Deja Vu fonts, some others have installed Windows fonts to get it looking the way they like.

---

### Post by jiminycricket on 2007-05-01
ITA: There's [https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend) and [https://wiki.ubuntu.com/SupportAllSuspendMethods](https://wiki.ubuntu.com/SupportAllSuspendMethods) which seem to have some help .  You should be able to change the driver to 'nv' in /etc/X11/xorg.conf to see if you can suspend..although make a backup of it beforehand.

Also, if you can, send something called 'dumps' to the [Nouveau ]("http://nouveau.freedesktop.org/wiki/")project for free 3d drivers for all nVidia cards, see the link in my sig.  3d cards that free  open source drivers, if they have these issues at all, can be fixed by developers, whereas nVidia's and ATI's drivers are closed source and take a long, long time (almost a year in one case) to fix their issues.

---

### Post by [ITA]ArgH on 2007-05-01
> **jiminycricket said:**
> ITA: There's [https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend) and [https://wiki.ubuntu.com/SupportAllSuspendMethods](https://wiki.ubuntu.com/SupportAllSuspendMethods) which seem to have some help .  You should be able to change the driver to 'nv' in /etc/X11/xorg.conf to see if you can suspend..although make a backup of it beforehand.

Also, if you can, send something called 'dumps' to the [Nouveau ]("http://nouveau.freedesktop.org/wiki/")project for free 3d drivers for all nVidia cards, see the link in my sig.  3d cards that free  open source drivers, if they have these issues at all, can be fixed by developers, whereas nVidia's and ATI's drivers are closed source and take a long, long time (almost a year in one case) to fix their issues.han

thanks to all for your replies! i found this on the page you suggest me > Fix nonfree drivers

Many users report problems suspending their laptops with the nonfree nvidia and ati video drivers. Since installation of these drivers will likely be the default option in Feisty, improved suspension would be a great boon. The inclusion of certain boot-time options (e.g. agp=no for nvidia), xorg.conf options (e.g. Nvagp=1 for nvidia)_** and suspend options (e.g. “[U]ProcSetting extra_pages_allowance 10000” for suspend_2/hibernate**[/U]) can sometimes ease these issues. But in many cases even these efforts will fail. If ubuntu is really going to rely on these nonfree drivers, we need to exert more pressure on nvidia and ati to get their drivers to comply with the kernel's power management policies.


mmm where can i change the underlined one?

---

### Post by 1two34 on 2007-05-01
You can control some services with sys-config ( at least on Dapper)  try this one [http://ubuntuforums.org/showthread.p...highlight=boot](http://ubuntuforums.org/showthread.p...highlight=boot)

---

### Post by [ITA]ArgH on 2007-05-01
> **1two34 said:**
> You can control some services with sys-config ( at least on Dapper)  try this one [http://ubuntuforums.org/showthread.p...highlight=boot](http://ubuntuforums.org/showthread.p...highlight=boot)

mmm this one point the index forum:lolflag: :lolflag:

could you plese post the link again?

---

### Post by [ITA]ArgH on 2007-05-02
no one with the correct link?

---

