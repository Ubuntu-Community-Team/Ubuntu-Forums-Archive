---
title: "How to install compiz-fusion? Help"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by The Patriot on 2008-03-07
I am new to Linux, so get it easy on me, I have a Kbuntu 7.04 installed and I am trying to get the desktop effect the one I saw in youtube on my laptop and I need help from u guys to how to install compiz-fusion or beryl (that's what they call it) I heard I need to install Nvidia card or something like thta for it to work, but I have  a ATI card???:confused: And by the way i was thinking about upgrading to Gusty but i was afraid cuz there were some issues problems I have been hearing about... thank u and I appreciate if some1 help me.

Cheers, The Patriot
(Sorry for my bad english)

---

### Post by spiderbatdad on 2008-03-07
Could you post the results of:```
lspci
sudo lshw -C video
```Feisty doesn't come with compiz-fusion. You used to be able to add beryl using Trevino's repositories, and frankly it worked much better on my system than compiz-fusion has. I don't know if those repos are being maintained any longer. But the results from those commands will give an indication as to how well compiz-fusion will work on your system when you decide to upgrade.

---

### Post by The Patriot on 2008-03-07
Thank u for the quick reply, because the guys at Kubuntuforum couldn't reply.And yeah i'm updating right now.I guess i have a change of heart. Here it is:



00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
nathan@ubuntu:~$ sudo lshw -C video

---

### Post by Tatty on 2008-03-07
Compiz-Fusion is basically the new name for beryl.  Beryl and Compiz were two related projects which got merged together to create CF.

Basic checklist to get compiz-fusion working the easiest way:

1. Install Gutsy
2. Install the best drivers for your card
3. Go to System->Preferemces (or Administration, cant remember which one)->Appearance  then enable the effects

---

### Post by spiderbatdad on 2008-03-07
Not sure about getting the driver to run 3D acceleration for this card in Kubuntu...I'm assuming compiz-fusion is your goal. A number of guides exist for this card on Ubuntu. Kubuntu has essentially the same packages such as xorg-driver-fglrx or search synaptic for ati binary xorg drivers: use the search utility to make it easy. They are usually with the xserver packages.
Anyway good luck. You need a fair amount of ram for a good experience. Hopefully you have at least  1GB.  You're probably going to have to read a few guides before deciding on your approach. What works on one system doesn't always work on another...even with the same graphics card.

---

### Post by The Patriot on 2008-03-07
how do install the best card for my driver? Only 30 mins, before completion installing Gusty

---

### Post by spiderbatdad on 2008-03-07
did you go with KDE or Gnome?

---

### Post by The Patriot on 2008-03-07
KDE of course. I think, Like I say i'm a new linux user, so I don' t really know exacty. Can't wait to try Gusty.:)

---

### Post by eduardoeltortuga on 2008-03-07
Just open Kubuntu's help documentation. Then under Kubuntu documents you'll see system documents.  Then under desktop configuration It explains how to install compiz fusion. When you install , also install emerald. 
     Emerald is window decorations. You need to also install subversion to get more window decorations from the emerald repositories. 

 Good luck:)

---

### Post by spiderbatdad on 2008-03-07
There are some issues running it on kde. This blog quickly notes additional packages you'll need from synaptic. You'll probably want the xorg-driver-fglrx, but I'm not positive. It's easy enough to remove provided you install everything via synaptic.

[http://blog.turbulentsky.com/2007/10/fix-compiz-fusion-on-kubuntu-710-gutsy.html](http://blog.turbulentsky.com/2007/10/fix-compiz-fusion-on-kubuntu-710-gutsy.html)


As I said if that driver doesn't work for you, look into the binary ati xorg drivers, also in synaptic.
Remember to reboot in between trying different drivers.

---

### Post by The Patriot on 2008-03-07
Hey guys, I think the update to Gusty is done but before I do that, a little help here,saying that i should remove or not the obsolete packages or skip it??

---

### Post by khmer04sti on 2008-03-07
Not sure where you're at in your installation. I just recently did this today and I followed this ([http://forum.compiz-fusion.org/showthread.php?t=5302]("http://forum.compiz-fusion.org/showthread.php?t=5302')) guide and it works perfectly on my system. I'm using an nVidia 7 series card but it should work with ATI cards given that you install ATI's most recent drivers.

---

### Post by The Patriot on 2008-03-08
Lol, it seems to work but now the "minimize and maximize" feature and its toolbar doesn't appear. and where can I find the shortcut key for compiz-fusion. Thanks...

---

