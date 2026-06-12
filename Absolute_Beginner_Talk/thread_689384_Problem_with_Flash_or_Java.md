---
title: "Problem with Flash or Java"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Ohioan on 2008-02-06
WARNING: I'm completely and utterly new to Ubuntu.  I am a total newb.  I can open a terminal and know to use sudo.  I also know how to use synaptic.  Other than that, I'm lost.

Now, I have a problem with flash or java, I'm not really sure which.  But, when I go to the Verizon Wireless webpage ([www.vzw.com](www.vzw.com)) Most of the interactive screens are completely grey. (screenshot to become available this evening).  

I've tried following the Multemedia How-To guide in the multimedia/streaming forum but it hasn't helped.  I'm lost and would like some help.

Thanks!

---

### Post by philinux on 2008-02-06
Thats flash

you need this.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

Uninstall any flash you have installed first.

---

### Post by Ohioan on 2008-02-06
I tried that once and it didn't work.  I'll try'er again when I get home though..

---

### Post by seventhc on 2008-02-06
here's the one I always use and it has always worked, so if the previous one fails try this one.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
download the first file, then scroll down for easy to follow instructions. :)

---

### Post by gandaran on 2008-02-06
the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

gandaran

---

### Post by seventhc on 2008-02-06
> the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install
I agree but this way has never worked for me on 2 different machines. I have no idea why it works for so many but not for some, my only solution is to use as I posted above, it's one of the first things I install on a fresh ubuntu install.

---

### Post by Ohioan on 2008-02-06
Thanks Gandaran! That worked like a charm...  I love you!

---

