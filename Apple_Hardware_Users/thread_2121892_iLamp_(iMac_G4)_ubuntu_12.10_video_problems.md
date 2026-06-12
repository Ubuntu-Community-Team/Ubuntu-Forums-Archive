---
title: "iLamp (iMac G4) ubuntu 12.10 video problems"
date: 2013-03-03
forum: Apple Hardware Users
---

### Post by OneCrackedEgg on 2013-03-03
Hello, gang - 
Downloaded the Lubuntu 12.10 Alternate ISO; installed it (successfully, I think) on the following iLamp (iMac G4) system:
- 700MHz, 128MB RAM, 40GB HDD. Was previously running OS X 10.4. NO IDEA what video card it had in it.

Installation of Lubuntu Alternate ISO (from [http://cdimage.ubuntu.com/lubuntu/releases/quantal/release/](http://cdimage.ubuntu.com/lubuntu/releases/quantal/release/)) went painlessly. However, after the system reboot, I got the following:
1. Initial bootup
2. hit "Enter" to boot into Linux
3. nearly the entire screen went thru this nice bright beige-ish color to a darkish blue and then black, fading in gradually. It just sits at that screen, doing nothing. It's been nearly 10 minutes so far and I'm feeling like a dork. 

Cycling the power on the system does exactly nothing, just brings me back to the same spot after the same steps. 

Does anyone have ideas for how I can get past this? I'm definitely open to other versions of the OS, just need a gentle shove in the right direction.

Thanks in advance.. /oce

---

### Post by danield on 2013-03-04
iLamps are notoriously difficult to get video working on.  A 700MHz model has a GeForce2 MX graphics card, so you'll want to read the [Configure Graphics section]("https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics") of the PowerPC FAQ, specifically anything having to do with Nvidia and nouveau.  There's also an [Nvidia sub-section]("https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards").

Sorry I can't give more specific help, but I've only dealt with ATI cards.  I have it easy.

---

### Post by str8bs on 2013-03-04
Maybe try-
boot: linux nouveau.modeset=0 xforcevesa
If that gets a GUI (likely unreadable due to low color), you may be able to increase the depth with xorg.conf .

If you have the time, you may want to instead try the 12.04 xubuntu iso rsavage posted [here]("http://ubuntuforums.org/showthread.php?t=1918246&page=23&p=12540750&posted=1#post12540750"). Make sure and check the readme file on the iso.

---

### Post by Brian Kendig on 2013-03-19
I'm running into the same problem.

Try booting with "Linux nomodeset" at the yaboot prompt. That will at least get you video, but the colors are all messed up so it's unusable. At the initial display where you see nothing but a mouse pointer, just type your password and press return; that will bring you to a desktop.

I understand that the solution to the messed up colors is to change the display bit depth from 8-bit to 24-bit, but I haven't been able to figure out how to do that.

---

### Post by este.el.paz on 2013-03-19
> **str8bs said:**
> Maybe try-
boot: linux nouveau.modeset=0 xforcevesa
If that gets a GUI (likely unreadable due to low color), you may be able to increase the depth with xorg.conf .

If you have the time, you may want to instead try the 12.04 xubuntu iso rsavage posted [here]("http://ubuntuforums.org/showthread.php?t=1918246&page=23&p=12540750&posted=1#post12540750"). Make sure and check the readme file on the iso.

Gents:

I spent a lot of time trying to get a working Linux system on my iLamp 800, with a lot of help from numbers of different people--it ain't easy, unless you take str8's advice and roll back to the Xu 12.04 iso, where he even posted the link for you.  I recently tested the .iso out on my computer (which is sick) and it works just fine . . . I think I needed the "live nomodeset fbforcenv" parameters to get it to work.  The ilamp uses the nv driver, and the main editions of Linux are not including the nv driver, I had to do a fairly complicated process in the Terminal to retro-install the nv driver . . . but rsavage has done that already in this specific .iso version of Xu 12.04 tweaked for PPC.  I'm using it now in my iBook.  My suggestion is to take str8's advice . . . or turn away and/or suffer as you try to get 12.10 to work . . . then the other question is whether the OP has enough RAM . . . 128 might not be enough???  Don't know, my iMac has 512MB and seems to have a problem with suspend, otherwise, the screen is OK.

e.e.p.

---

### Post by Brian Kendig on 2013-03-19
What tweaks did he make in that iso? Any chance those changes might make it into 13.04?

---

### Post by este.el.paz on 2013-03-19
> **Brian Kendig said:**
> What tweaks did he make in that iso? Any chance those changes might make it into 13.04?

@BK:

Special tweaks . . . tweaks that are specially tweaked for PPC . . . which needs a different kind of tweak than your ordinary tweak . . . .  : - )  I can't say what they are, firstly because I don't know too much except how to get the system installed and use it as GUI, and then use Terminal to upgrade . . . .  It was posted in thread #226  from the link that Str8bs posted in this thread, but after Iposted here I was trying to find something about the indexing app that was recommended to be removed, and I saw that the .iso for Xu 12.04 has been removed . . . perhaps it's now just part of the PPC file for Xubuntu 12.04.  As far as whether rsavage will be turning his tweaking hands to 13.04, you'd have to ask him . . . .  If I find out what happened with the.iso, I'll try to post back here, but maybe just go to the Xubuntu downloads.

e.e.p.

---

