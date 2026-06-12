---
title: "Compiz Won't Work!! Help please"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by s0L1Tud3 on 2008-04-08
Hey, I am new to Ubuntu/Linux , and I tried installing Compiz , following the directions on this website: 

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Everything worked out fine, except when i did the last step to run compiz, it just rearranged my desktops (i had 6, it changed it to 2), and also whenever i open an App such as Kopete (in an empty desktop), everything else that is open in other desktops will come up! Also, I can no longer use the scroller on my mouse to switch desktops!! 
Aside from that, nothing changed... It seems to have made it worse! Does anyone have any ideas of what I should do? Here are my specs:

$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
01:06.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:06.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


BTW, when I go to System / Screen & Graphics, it has me using "intel experimental modesetting.." for my graphics card .. I tried finding mine on the list but I couldnt.. Either way, everything has worked fine until I tried installing Compiz and now its just worse!

 Any ideas would be greatly appreciated, I checked the forum and couldn't find anyone with the same situation as me... Thanks guys

---

### Post by twist2b on 2008-04-08
do you have gusty or fiesty?
its obviously your graphics card. Find a tutorial out there for your brand
can you post your EXACT graphics card type AND if your using Feisty or Gusty?
Also, I suggest a better install of Compiz. COMPLETELY REMOVE compiz in synaptic

---

### Post by s0L1Tud3 on 2008-04-08
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) 

^ I believe that is my graphics card... How do I know if I'm using Feisty or Gusty? I just downloaded it right off the main ubuntu website, Ubuntu 7.10 i386

I'm not really sure how to do a better install, that was the best one i could find on google. I'm really new to linux commands and stuff.. I couldn't find any sort of tutorial with my model card except : [http://ubuntuforums.org/archive/index.php/t-675870.html](http://ubuntuforums.org/archive/index.php/t-675870.html)

and that didn't really help me much because he was having a slightly different problem than me.. Mine already says it is "intel -experimental modesetting driver" .. but I'll go ahead and remove compiz now..

> **twist2b said:**
> do you have gusty or fiesty?
its obviously your graphics card. Find a tutorial out there for your brand
can you post your EXACT graphics card type AND if your using Feisty or Gusty?
Also, I suggest a better install of Compiz. COMPLETELY REMOVE compiz in synaptic

---

### Post by conscious on 2008-04-08
7.10 is codenamed Gutsy Gibbon. It has compiz installed by default.

---

### Post by s0L1Tud3 on 2008-04-08
oh  really? How do i use it? BTW when I searched "compiz" in Synaptic, there are so many things that showed up, I dont know which I installed earlier and what was already there... And when i typed "compiz" in terminal, it says this:

$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by halln on 2008-04-08
It's on add remove, drp down all open source then type ccsm

---

### Post by Therion on 2008-04-08
Everything you need to know:  [How to Setup Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).  Step by tiny step...

Free bonus links:  What all those [Animations](http://wiki.opencompositing.org/Plugins/Animation) do and what the [Main Plugins](http://wiki.opencompositing.org/PluginsMain) do.

---

### Post by s0L1Tud3 on 2008-04-08
> **halln said:**
> It's on add remove, drp down all open source then type ccsm

UGHHH well I typed that in and it said nothing was found. I did apt-get remove compiz .. and rebooted X... and it's even worse! Now scrolling and moving windows is really really lagged, and its still not back to how it was before I started.. I am so lost

---

### Post by s0L1Tud3 on 2008-04-08
Oh, sorry I missed the "open " part with ccsm, Yeah I just deleted the Compiz Config wizard (thats all that came up).. but everything is so slow still! Is there anyway I can fix this?

---

### Post by conscious on 2008-04-08
If you have followed the instructions at [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml), you probably now have Feisty package installed, which is no good. I suggest you undo the addition of the third-party software source (remove it at System -> Administration -> Software Sources), then restore the officially packaged compiz:
```
sudo apt-get update
sudo apt-get install compiz
sudo apt-get upgrade
```

It's also very handy to install ccsm. Make sure you have "universe" repository enabled at System -> Administration -> Software Sources, then do
```
sudo apt-get install compizconfig-settings-manager
```

This will make settings manages available under System -> Preferences -> Advanced Desktop Effects Settings.

---

### Post by st0n3cutt3r on 2008-04-08
are you using a restricted video driver?  Try turning the driver off if you are

---

