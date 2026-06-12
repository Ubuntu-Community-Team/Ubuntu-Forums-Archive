---
title: "iMac 10.1 (21.5in) Screen problem after Lucid upgrade"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by xvila on 2010-04-30
Hi,

This is for an iMac 10.1 (21.5 inches)
I just upgraded from Karmic to Lucid via a regular network upgrade.
Everything went (apparently) well. I accepted every configuration update (those warnings saying that your customized configuration will be trashed), specially the one for Grub2

After rebooting, thought, nothing works. Grub is loaded, I see the menu, but no matter what I choose (even "Recovery mode" entries) the screen goes black, no splash logo whatsoever, no text, nothing.
No console login is available to try a manual fix.

I can boot from a CD and use a Live system, but I have no idea what to fix in my installed system

Any ideas ?

Xavier

---

### Post by zeroti on 2010-04-30
You could try reinstalling from a CD. I don't know if that would fix it, but it's worth a try.

EDIT: I just read somewhere that you can't upgrade an install from a Live CD, only a fresh install. So you'd have to use an alternate install CD.

---

### Post by xvila on 2010-04-30
> **zeroti said:**
> You could try reinstalling from a CD. I don't know if that would fix it, but it's worth a try.

EDIT: I just read somewhere that you can't upgrade an install from a Live CD, only a fresh install. So you'd have to use an alternate install CD.
Thanks a lot. I will try on Monday (it's on my office)

---

### Post by heykenen on 2010-04-30
When I try to install from CD screen goes black.

iMac 27" i7.

---

### Post by xvila on 2010-04-30
> **heykenen said:**
> When I try to install from CD screen goes black.

iMac 27" i7.
You mean after the upgrade or it doesn't even boot from the LiveCD ?

---

### Post by heykenen on 2010-04-30
No, I try to do a clean installation. It boot from CD, I chose language.  After,  when I chose "Try Ubuntu ... " screen goes black and I can hear cd is loading but screen is always black.

---

### Post by xvila on 2010-04-30
> **heykenen said:**
> No, I try to do a clean installation. It boot from CD, I chose language.  After,  when I chose "Try Ubuntu ... " screen goes black and I can hear cd is loading but screen is always black.
This is very strange. At least I am able to completely boot from the installation CD, all the way to the plasma desktop (it takes a while, though)
My guess is that it has something to do with the graphic card, but I have no idea.
I wish someone more knowledgable could provide some helpfull hint

---

### Post by majortom67 on 2010-07-02
> **heykenen said:**
> When I try to install from CD screen goes black.

iMac 27" i7.

Same problem here. I've been reading that pressing F6 at the first screen (choose live, install....) will prompt you a menu where you can choose "nomodeset" (if it doesn't work just add the fllowing at the the text line at the bottom: "radeon.modeset=o nomodeset"). The instalation should proceed with standard graphics and let you work in that way for one session. In that session you can download the correct ATI drivers.
Unfortunately for me the problem seems to be elsewhere, in the boot method.

I've been also reading that beta 2 works, Unfortunately for me, AGAIN, the installer works nice (very very very slow, bythe way) but crashes when I choose the partition to place Kubuntu. I don't know if this is because I have Mac OS X in the first partition, epmty 2nd part for Ext4, empty 3rd partition for SWAp and last partition with Win 7 (which, by the way, may not work anymore).

I'm really bored about all these problems and I'm not sure are related to Apple's hardware.

---

### Post by adamwitherspoon on 2010-11-02
Same issue on 27" i7 iMac circa late 2010. Installing 9.10 then perfromed upgrade.
Also noted LVM is not supported (afaik).
I am going to install again, and try to install updates for the drivers first. I think this is a known issue with the graphics drivers.

This is what I found:

The default 10.04 ISO won't boot with a compatible driver for 2010 iMacs, so use one of the following solutions: 

[LIST]
[*]Boot and install 9.10, install the proprietary ATI driver then upgrade to 10.04 
[*]Download [Ubuntu Alternate installer]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download"), which runs in text mode. Once Ubuntu is installed: 

[LIST=1]
[*]Reboot and in GRUB menu highlight Recovery Mode 
[*]Edit kernel parameters and add *radeon.modeset=0 nomodeset* 
[*]Boot and choose 'Low Graphics Mode' when problems reported 
[*]Install the proprietary driver using *System > Administration > Hardware Drivers* 
[/LIST]
[*]Use an external monitor connected to the HDMI output.
[/LIST]

---

