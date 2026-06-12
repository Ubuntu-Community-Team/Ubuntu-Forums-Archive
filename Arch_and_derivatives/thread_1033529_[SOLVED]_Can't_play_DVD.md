---
title: "[SOLVED] Can't play DVD"
date: 2009-01-07
forum: Arch and derivatives
---

### Post by Dr Small on 2009-01-07
Arch has always worked well with playing DVDs, and it still does. But my Mom bought a DVD series, and they won't work on Arch or Ubuntu. They work fine in Windows Media Player or PowerDVD, but not on any Linux computers.

I mounted the DVD to /mnt/dvd, opened VLC to open the directory (since it protests (and always has) that it can't open the device /dev/dvd). This is how I always watch DVD.

This time around, VLC just freezes. Tried to get some output from the terminal, and it produces no errors. For the record, the DVD contains almost 8GBs of data.

I have libdvdcss, libdvdread and libdvdnav and other DVDs work too. It's just odd that these should not work. I have only tried VLC since that's all I have. I can't try mplayer at the moment since I need to do some serious upgrading to get mplayer and other applications to work, so that's out of the question right now.

(My last encounter with an upgrade + kernel resulted in a fresh reinstall, so before I try it again I plan to have a recent download of Arch to try).

Any thing else I could try?


**EDIT** I just tried a different DVD that used to work, and it doesn't so something is broke somewhere. I am now attempting to upgrade VLC, but at this point, I fear it will break also.

---

### Post by MisfitI38 on 2009-01-07
> **Dr Small said:**
> 
I mounted the DVD to /mnt/dvd, opened VLC to open the directory (since it protests (and always has) that it can't open the device /dev/dvd). This is how I always watch DVD.



I can help you with this one small piece. Instead of trying to open /dev/dvd, use /dev/sr0 on Arch.

---

### Post by Dr Small on 2009-01-07
Tried that, same thing.
I have been trying everything I know, and finally got the DVDs to work by opening the disk, selecting Browse for Disc Device, select the /mnt/dvd/VIDEO_TS directory, and it works, but no menus.

I have a feeling that libdvdnav is broke (probably a dependency issue somewhere) and that's what the whole problem is. Alot of my problems would probably go away if I upgraded.

Thanks for the tip!

Dr Small

---

### Post by stanca on 2009-01-07
Try install ogle or quickstart.

---

### Post by Dr Small on 2009-01-07
> **stanca said:**
> Try install ogle or quickstart.
ogle worked fine for my regular DVDs. I actually like it. I'll probably be using it from now on. But it wouldn't work with my new DVDs. Here's what it kept complaining:

```
libdvdread: Invalid IFO for title 4 (VTS_04_0.IFO).
libdvdread: Invalid IFO for title 4 (VTS_04_0.BUP).
FATAL[ogle_nav]: ifoOpenVTSI failed
```

And I couldn't find quickstart, so I never tried it.

---

### Post by smartboyathome on 2009-01-09
Could the DVD be using newer DRM encryption? I know that I bought Wall-E to watch it on my computer as well as my TV, but it doesn't work because of the newer DRM.

---

### Post by Barrucadu on 2009-01-09
I know your installation is fairly out of date due to problems with a particular kernel version, so assuming whatever it was is fixed in a later version follow these tree steps for *fun* :D

1. Backup.
2. Attempt *massive* upgrade on every package you've held back.
3. Pick up the broken pieces and make it live again.

---

### Post by Dr Small on 2009-01-09
> **smartboyathome said:**
> Could the DVD be using newer DRM encryption? I know that I bought Wall-E to watch it on my computer as well as my TV, but it doesn't work because of the newer DRM.
It could I guess. It has the anti-copy symbol on the bottom of the box, but I thought I read somewhere about 1995 on it. So I didn't think it would have any new encryption that hasn't already been broken. I mean, I can watch the DVD, but the menu's just don't work on it.

---

### Post by Dr Small on 2009-01-09
> **Barrucadu said:**
> I know your installation is fairly out of date due to problems with a particular kernel version, so assuming whatever it was is fixed in a later version follow these tree steps for *fun* :D

1. Backup.
2. Attempt *massive* upgrade on every package you've held back.
3. Pick up the broken pieces and make it live again.
Trust me, I'm already planning all of that for *fun*! :D It's starting to get boring having a completely usable system, so I need something to break to fix it. Upgrading may just do the trick ;)

---

### Post by Nepherte on 2009-01-10
Certainly give dvdread and dvdnav from aur a try if you haven't already.

---

### Post by Dr Small on 2009-01-10
> **Nepherte said:**
> Certainly give dvdread and dvdnav from aur a try if you haven't already.
I generally miss the obvious. I totally forgot about looking for newer version on the AUR. I must say, that really helped! Now VLC works (and I'm sure ogle will work too). Thank-you. I really appreciate that help! :)

Now opening DVDs with VLC works like it should just by opening the disc, and the new DVDs work with the menu. I am satisfied. But, I still need to upgrade and risk breaking all of this to get a couple other applications to work that broke when I upgraded other stuff! :D

Thanks again.
Dr Small

---

### Post by Nepherte on 2009-01-11
> **Dr Small said:**
> I generally miss the obvious. I totally forgot about looking for newer version on the AUR. I must say, that really helped! 
Like everything that comes from the mplayer devs, only old versions are included in distro repositories. For mplayer it's just because they use svn instead of releases. No idea why dvdread and dvdnav are like that, but the version difference between aur and extra is huge: 0.9.7 vs 4.1.3

---

