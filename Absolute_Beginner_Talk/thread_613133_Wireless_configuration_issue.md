---
title: "Wireless configuration issue"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by spoon_uk on 2007-11-14
Hi,

Complete noob here. I've just installed Ubuntu. No problems with installation (great). Configured wireless settings and now the machine doesn't seem to boot. The machine seems to halt after the loading screen reaches about 80% and then throws me into a boot sequence screen where the last item in the list is 'Starting Common Unix Printing System : cupsd'. Doesn't get any further.

I'd like to become more familiar with Linux however this issue seems to have steered me back towards Windows. Any help would be greatly appreciated.

Cheers!

Vince

---

### Post by gregthebunny on 2007-11-14
My first instinct and suggestion would be to simply install Ubuntu again. The _[**C**ommon **U**nix **P**rinting **S**ystem](http://en.wikipedia.org/wiki/CUPS)_ **D**aemon has nothing to do with your wireless configuration.

You could also try booting into single user mode and disabling the cupsd service. Here's a good article describing run levels and services: _[Debian and Ubuntu Linux Run Levels](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)_. See also: _[Grub - specify runlevel](http://ubuntuforums.org/showthread.php?t=271800)_ to specify the run level at boot.

---

### Post by tato97 on 2007-11-14
I have exactly the same problem. Installation went w/o problems. I changed the wireless settings to create a manual Wireless connection with WPA security. Re-booted the machine. Now the system wont' boot. It hangs on the line:

* Starting Common Unix Printing System: cupsd

Several lines above it states network installation [OK] however something tells me the error has to do with the network changes. 

I don't remember how to list the running processed to kill the one that's hanging the system or if even that's possible.  I use to work with Unix MANY moons ago...

Any help would be appreciated

Thanks

---

### Post by spoon_uk on 2007-11-15
I did try reinstalling and experienced exactly the same problem. I didn't try configuring anything else on the system so the issue is definitely related to setting up the wireless network.

I also noticed that the machine became unstable after attempting to configure wireless networking.  For example, I couldn't seem to open the network settings dialogue to undo the changes I'd made and the computer refused to shut down. I certainly can't see how making such minor changes could affect the stability of the machine in this way.

I think I may try a wired connection next time.

---

### Post by FokkerCharlie on 2007-11-23
Hi All

I've been having *exactly* the same problem.  No probs installing, but tweaking the WLAN settings in Network Manager seems to crash the computer, and the re-start fails at CUPSD.   The only way that I have found to get a response from the computer is by hitting the power button- Ubuntu starts to power-down gracefully, but then stops with a comment about wpa_supplicant.

This is very interesting- it is natural to suppose that CUPSD has nothing to do with networking, but wpa_supplicant certainly does!
 
I'd love an answer on this.  By the way- I'm effectively a complete newb, so apologies if the terminology isn't correct!

Charlie

---

### Post by boarder on 2007-12-14
I have installed 7.10 desktop edition on my pc and am getting exactly the same problem as mentioned by everyone above.  Have tried a reinstall and exactly the same thing happens.

I really want to use ubuntu but its useless without WPA wireless.  I tried the fix as mentioned in "Bug #48263 in Ubuntu" but now system wont start and hangs at the following point

* Starting Common Unix Printing System: cupsd

Can I just remove cupsd from my system if I am not planning to do any printing?  Any help would be much appreciated.  If more info is needed please let me know...

---

### Post by FokkerCharlie on 2007-12-15
Hi Boarder

I'm new to Linux, but I removed CUPSD from System>Administration>Sessions, and it had no adverse effect while I was fiddling with my network settings.  When I needed to print, I had to re-enable CUPSD, but it has not caused a problem since I got the WLAN/WPA sorted out.

Hope this helps.
Charlie

---

### Post by weblordpepe on 2007-12-15
Damn CUPS caused my upgrade to gutsy to completely bomb, and ruin my entire system making it only bootable to single-user mode. 

It was NOT fun using XP to rescue a Ubuntu install.

---

