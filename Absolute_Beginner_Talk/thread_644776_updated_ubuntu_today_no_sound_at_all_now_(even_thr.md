---
title: "updated ubuntu today: no sound at all now (even through headphones)"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by agerg on 2007-12-19
As the title suggests I just updated and what little bit of sound I did get (through headphones) is totally gone now :(

My volume control icon has a little red cross next to it and I'm told:
"No volume control GStreamer plugins and/or devices found." on the dialog box when I double click the icon

Any suggestions?

---

### Post by lvleph on 2007-12-19
> **agerg said:**
> As the title suggests I just updated and what little bit of sound I did get (through headphones) is totally gone now :(

My volume control icon has a little red cross next to it and I'm told:
"No volume control GStreamer plugins and/or devices found." on the dialog box when I double click the icon

Any suggestions?

What type of sound card? If it is Intel HDA STAC92XX, then the linux backports for 2.6.22-14 will be the solution.

---

### Post by agerg on 2007-12-19
well the HDA part sounds familiar but entering aplay -l into terminal gets me:
```
greg@greg-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...

```
Not sure what to do with your solution (total novice)

---

### Post by lvleph on 2007-12-19
Post the out put from lspci.

---

### Post by agerg on 2007-12-19
ok...the output from lspci:
```
greg@greg-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

```

---

### Post by mmb1 on 2007-12-19
Type "sudo alsamixer" into the terminal and post the output.

---

### Post by agerg on 2007-12-19
ok...the output from sudo alsamixer:

```
greg@greg-laptop:~$ sudo alsamixer
[sudo] password for greg:

alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by mmb1 on 2007-12-19
Alright, this definitely means that your OS doesn't recognize that you have a sound card.

Everything worked alright before the upgrade?

---

### Post by mmb1 on 2007-12-19
This might be a driver issue, if you know the name of your sound card, search for packages that are labeled with it in synaptic.

---

### Post by agerg on 2007-12-19
Well I had sound coming only through the headphones before the update, I tried various fixes but none worked.

As for my soundcard the only thing I know about it is what I got from the output of lspci:
```
SB450 HDA Audio
```

edit: I'm betting sb450 doesn't identify my soundcard, more it identifies where it is in my laptop, though I might be wrong

---

### Post by mmb1 on 2007-12-19
Alright, I was unable to find any packages related to your specific card, but you may want to check and see in synaptic that you have "alsa" installed.

On a side note, could this be a speaker issue?

---

### Post by agerg on 2007-12-19
hmm...I installed the latest version of alsa yesterday.
With respect to my speakers, one feature of the problem I had before this problem was that in volume control I only had the headphones in the switches tab.

I'm trying to get some specs from the web about my laptop (acer aspire 5050) hoping to find the specific model of soundcard inside it but having no luck so far :(

---

### Post by mmb1 on 2007-12-19
In your sound preferences, at the bottom, there should be a menu labeled device under the devices tab.  See if the OSS mixer is available, if it is, click it and see if you get sound.

---

### Post by agerg on 2007-12-19
tried that...got nothing. there is little way to do anything you'd associate with having sound (can't adjust volume etc...) :(

---

### Post by mmb1 on 2007-12-19
This seems to be a problem that was caused by the update, I'm helping another person who udpdated and had sound trouble as well.

Here's the thread, maybe we'll find a solution to the problem:[http://ubuntuforums.org/showthread.php?t=645129](http://ubuntuforums.org/showthread.php?t=645129)

---

### Post by agerg on 2007-12-19
re-installed alsa again and got my sound problem back to where it was before the update :) (only plays through headphones) I think I'm going to admit defeat on this one and graciously accept what I'm given

Thanks for your help :)

---

### Post by lvleph on 2007-12-19
There is a bug report about this, if it is the same problem I was having. It sounds like the same problem. What you want is the linux-backports-modules 2.6.22-14. You can get that from Synaptic.

---

### Post by agerg on 2007-12-19
I have just had a look in synaptic and am warned in the description of the application:
"**Ubuntu supplied Linux modules for version 2.6.22 on i386**
This package contains modules supplied by Ubuntu for Linux kernel 2.6.22 on
i386.

You likely do not want to install this package directly. Instead, install
the linux-386 meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed."

I'm slightly worried about just installing from here, and don't know where to find this meta package...any suggestions?

---

### Post by CulleyS on 2007-12-19
The same thing happened to me today as well.  I have an Audigy 2zs Platinum sound card.

I hate to sound stupid, but as I've never done this before, how do I install the linux backports from synaptic?  I may know how to do this, but what is being said here isn't ringing any bells.

Thanks,

Culley

Edit: Figured it out.  Searched Synaptic Package Manager for "backports."  Testing now.  I was in the same situation, no soundcard detected.

Edit 2: Rock on, installing the backports restored my soundcard to working order.  Thanks for the posted fix.  I'll have to keep this in mind for future glitches upon upgrade.

---

### Post by mmb1 on 2007-12-20
> **agerg said:**
> Thanks for your help :)

No problem :)

This seems to be a common problem, I'm sure someone filed a bug report and we'll get a fix relatively soon.

---

### Post by lvleph on 2007-12-20
Bug report was filed during beta testing of Gutsy. The fix was the backports. As far as I know this will be the solution.

---

