---
title: "[SOLVED] Installing Flash on iMac G3"
date: 2007-08-03
forum: Apple PPC Users
---

### Post by Lurcher on 2007-08-03
I have checked for posts involving installing Flash on an iMac/500 (PPC).  The majority of them seemed to cover Windows-based systems, while others appear to be successful, though the message I get when I try to install the Flash installer for PPC is:

 '/home/bmcneal/Desktop/install_flash_player_9_linux/flashplayer-installer' 

ERROR: Your architecture, \'ppc\', is not supported by the Adobe Flash Player installer

The problem I am having is that, since ubuntu isn't supported by the Flash installer for Linux, and ubuntu doesn't recognize the installer for OS X, then how are PPC users to get the benefit of Flash?  Under Tiger (OS 10.4.10) I took such things for granted; under ubuntu (Feisty Fawn) I am just realizing how many sites that I tend to frequent use a  significant amount of Flash content (Sci-Fi.com in particular).

My primary system is an iMac G5, buy it is currently being repaired.  Thank -- insert deity of choice -- ______________  for Applecare I should be getting it back soon, but I don't mind trying to make my way around ubuntu.

As usual, thanks in advance :confused:

---

### Post by pxwpxw on 2007-08-04
Maybe gnash?
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnash&searchon=names&subword=1&version=all&release=all")

---

### Post by aysiu on 2007-08-04
**Step 1**
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**
Install Gnash ```
sudo apt-get update && sudo apt-get install gnash
```

**Step 3**
Close your web browser and then launch it again.

---

### Post by Auria on 2007-08-04
Actually it's not "Ubuntu that does not support flash on PPC" but rather "Adobe that refuses to release a PPC version of flash for linux" so there's little we can do - there is no way to get adobe flash on PPC linux. there are altrenatives like gnash and videodownloader (see PPC FAQ) but don't expect to get perrfect flash support.

> and ubuntu doesn't recognize the installer for OS X

You can't expect that to work, Ubuntu is not OS X, it is a totally different system, it surely can't read OS X programs.

---

### Post by tonyr on 2007-08-04
Some posts I have seen about this suggest that gnash version 0.8.0 is the one to go with. 
Unfortunately, the version distributed with Feisty (7.04) is 0.7.2.  The current version, called
'third alpha release' is available for download at [http://www.gnu.org/software/gnash/]("http://www.gnu.org/software/gnash/")

- tony

---

### Post by namtap on 2007-08-04
> **aysiu said:**
> **Step 1**
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**
Install Gnash ```
sudo apt-get update && sudo apt-get install gnash
```

**Step 3**
Close your web browser and then launch it again.

I have done this, but I still cannot get any flash content in my browser.  While it is kind of nice not to have to be bothered by any flash ads, it's very annoying to have Firefox tell me that I need a plugin every time I go to any page with flash content.  Of course, sometimes I *want* said flash content.

What could be wrong?

---

### Post by FredSambo on 2007-08-04
You actually need to install the mozilla-gnash-plugin (search in synaptic) after you install Gnash 0.8.0

I actually just did this last night!

---

### Post by namtap on 2007-08-04
Thanks.  It sort of worked, at least.

Most flash ads work (shutter), but most everything else doesn't display correctly at all.  Oh well, I suppose.

---

### Post by FredSambo on 2007-08-04
Yeah, it doesn't work very well on mine either.  I have the iMac G3 DV 400MHz (slot loader) with 512MB of RAM.

---

### Post by Auria on 2007-08-04
You just met one of the main reasons Ubuntu PPC is not the main OS of many people here, unfortunately

---

### Post by stmiller on 2007-08-04
Gnash 0.8.0 is available in Feisty Backports. 

Go to Applications>Add/Remove>Preferences>

Updates> Check 'unsupported updates' Feisty Backports

Close and reload if it asks. Now search in Add/Remove for gnash and install Gnash 0.8.0. 

Or just

sudo apt-get install gnash 

if you prefer the terminal and version 0.8.0 will install.


I made a note in the FAQs so if people ask you can point them there.

---

### Post by indelible on 2007-08-05
What´s really annoying about the situation is that Flash has *never* been properly supported on PPC, even in Mac OS.   Anyone who´s used the flash plugin on older hardware knows exactly what I´m talking about.  Try viewing even simple Flash on a G3 in Mac OS and then play the same thing on a similar vintage Intel processor with MMX.  It´s absolutely laughable how slow the flash player is on PPC hardware.  My old celeron 400 probably ran flash better than any PPC chip ever will.   I certainly don´t see Adobe expending any effort to optimize flash for PPC at this point, and they´re even less likely to release a linux PPC version, knowing the PPC macs are practically dead already.  Gnash is a great start, and a lot better than nothing, but If you surf the web with a PPC, well, Flashblock is your friend. :roll:

---

### Post by FredSambo on 2007-08-05
> You just met one of the main reasons Ubuntu PPC is not the main OS of many people here, unfortunately

Yeah, I just put Ubuntu on the Wife's old iMac G3 because OSX 10.1.5 just wasn't cuting it, and Ubuntu has proven to be a wonderful solution.  But yeah, I am glad Ubuntu for PPC isn't my main OS though.  LOL

---

