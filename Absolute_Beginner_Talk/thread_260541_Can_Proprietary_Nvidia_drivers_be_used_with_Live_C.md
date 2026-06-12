---
title: "Can Proprietary Nvidia drivers be used with Live CD?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by bankrupt on 2006-09-18
Hi all,

    I burned myself a copy of the Live CD so I can get my feet wet a little bit with this distro, but I'm having a little trouble with it.  When I try and run the first option "Run or Install Ubuntu", the screen with the "X" comes up and then turns dark red.  After a short bit, a cream colored bar with the Ubuntu logo shows up in the center of the screen and then it hangs and won't load any further.  The cream colored bar looks misrendered, like there's a problem with the video card.  Now, when I use the safe video mode option, the Live CD will boot all the way through and it works OK.  I'm using an eVGA 7800 GT card.  Is there a way to load the proprietary drivers while using the Live CD, or can I only do that after installing the distro?  What exactly is different about the safe mode option that allows it to boot fully compared to the first menu option which hangs?  Any help would be appreciated.  Here are my full system specs:

AMD 64 3200+ (~2GHz)
EPoX 9NPA +Ultra mobo (nForce 4 chipset)
2 Gig of Corsair value RAM
eVGA 7800GT
2X 250 GB Seagate HD
NEC-3540A DVD/CD-R

---

### Post by nudnik on 2006-09-19
I do not beleive you can make use of the drivers whilst using the Live CD. My suggestion would be to install to the HD and then use either the 8774 or 8762  Ubuntu Nvidia drivers in the repositories which are optimised for both Ubuntu and your card. I have a 7300GS, much lower end, but same family, and although performance is not quite as good as it would be using Windows XP, it is certainly far superior to something like Windows 98.

8762 is in the standard repository, but get the latest 8774, visit this page

[http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

I think the "safe mode" is employing something like VESA, a very generic configuration that will drive just about anything, similar to the Windows XP configuration before drivers are installed.

---

