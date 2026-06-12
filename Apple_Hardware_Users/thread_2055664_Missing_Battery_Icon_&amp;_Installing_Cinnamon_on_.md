---
title: "Missing Battery Icon &amp; Installing Cinnamon on a G4 Powerbook"
date: 2012-09-09
forum: Apple Hardware Users
---

### Post by standarshy on 2012-09-09
I'm having two issuses at the moment.   I can't seem to install the Cinnamon interface through PPA and I'm missing the battery icon.

As far as the battery icon goes, I've tried adding pmu_battery using gksudo gedit /etc/modules but that didn't work.

I've tried adding the official PPA for cinnamon then updating the lists. When enter sudo apt-get install cinnamon, it says "Unable to locate package cinnamon"

I'd appreciate any help I can get.  I forgot to mention I'm running Kubuntu 12.04

Thanks!

---

### Post by 2blue on 2012-09-09
I finally got the battery icon to work properly, just now !! I am in lubuntu: double click on the bottom taskbar: add/remove panel items - panel applets folder - add - battery monitor. Restart activated it properly. All simple when you get to know  the lxde functions, probably something similar with xfce. 

Initially I used the sudo command too which made the battery icon appear, but it didn`t activate it properly. 

Best of luck !

---

### Post by standarshy on 2012-09-10
hi 2blue,

I tried what you said for the battery icon and it partly works.  It will correctly tell me of the battery level but always thinks that the computer is plugged in, even when it isn't.  In other words, if I unplug my computer, it'll tell me that my battery is discarging and the powersource is "ac power" even when it is obviously battery power.

---

### Post by 2blue on 2012-09-10
I don't know what to do about that unfortunately, I need to do some searching. There are tutorials for installing cinnamon on Ubuntu on the web, you should be able to adjust it for the xfce desktop.

---

### Post by standarshy on 2012-09-10
2blue,

I have followed the tutorials. They do not work for me. I presume it has something to do with me using an older mac with a powerpc chip.

---

### Post by rsavage on 2012-09-12
> **standarshy said:**
> 
As far as the battery icon goes, I've tried adding pmu_battery using gksudo gedit /etc/modules but that didn't work.

The kubuntu equivalent would be 

```

kdesudo kate /etc/modules

```

> 
I've tried adding the official PPA for cinnamon then updating the lists. When enter sudo apt-get install cinnamon, it says "Unable to locate package cinnamon"

Most PPAs don't have PowerPC binary packages.  You'd have to download the source code and compile it yourself.  The FAQ has instructions to do this.  It maybe worth contacting the MintPPC people first to see if they've already compiled it.

---

### Post by standarshy on 2012-09-13
Thanks, I figured out the "kate" part.  

I may try to compile the source code. It's not something I've done often so I'll have to refresh.

The MintPPC guys are behind in the game. I reckon I'd have to just take care of it myself.  Thanks for the suggestion.

---

