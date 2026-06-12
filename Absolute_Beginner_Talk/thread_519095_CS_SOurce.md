---
title: "CS SOurce"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-08-06
So I'm having some difficulites with Counter-STrike Source! When I run wine followed by steam everything works great, I can get HL2 running fine, same with regular cs, but when I load up CS Source I get the main screen of the two guys and then as it loads it opens up to fullscreen and goes to a black screen. Nothing is locked up but I can't see anything, I can hear my mouse scroll over all the options and I have to find the bottom one via sounds to click exit and then hit enter. What can I do to change this so the screen comes up and expands as it should so I can set it to play properly? I'd appreciate any help! Thanks!! :):)

---

### Post by Rocket2DMn on 2007-08-06
Sounds like the game resolution and/or video stuff may be incorrect.
You can add commands to the loading of cs:s like -height, -width, -gl, -heapsize, etc...  I can't pull up the site right now to check since I'm at work and it is blocked, but you can google search for something like "counter-strike source command line options" or "counter-strike source launch options" and find different commands to test.
You can right click the game in steam and hit properties, then choose the tab for launching.
Add something like
"-gl -height 1024 -width 768" to force OpenGL and 1024x768 resolution.
If this gets you into the game, you can configure your video stuff from there, then remove the hardcoded launch options.

---

### Post by Tumpster on 2007-08-07
So i did that and got to set it to where my settings run well at and for some reason it just switches back to a black screen when I try running source again later. I'm having troubles with all steam games it would seem. Anyone else upgraded to the latest edition of wine and are now having troubles?

---

### Post by Rocket2DMn on 2007-08-07
I'm running wine 0.9.39 b/c later versions gave me a sound delay.  Are you trying to run direct3d?

---

### Post by Tumpster on 2007-08-07
Not that I know of, how can i completly remove wine and reinstall an earlier version. Another question, what is the best version of wine I should load???

---

### Post by Rocket2DMn on 2007-08-07
You can uninstall wine by running
```
sudo apt-get remove wine
```  If you use --purge you will wipe your ~/.wine folder which will delete all your games and whatnot, so I don't recommend it.
Older versions of wine are available in .deb packages online - [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
There is no "best" version, it's just whatever works for you.  Again, I use 0.9.39, but my graphics are not a problem, I just use it because of the sound issue I have in later versions.
If you use an older version and decide to keep it, you will have to disable the updating of wine in the package manager.  Open Synaptic and search for wine, then select it and go to Package->Lock Version

---

### Post by Tumpster on 2007-08-07
Alright, I've given that a try, here goes.......

---

### Post by Tumpster on 2007-08-07
So even before I switched to a new version, I'm getting all source games locking up. What could be causing this or what can be done to fix this? They will lock up on random to the point where I have to reboot. ANy ideas?

---

### Post by Rocket2DMn on 2007-08-07
Is it locking up during gameplay or right when you load the game, or right when you join a server?  Please be as specific as possible.
Run from terminal, and post any output you get after a crash (if possible).
PS: This is the guide I followed to setting up cs (though I used the deb file rather than their method).  They have some troubleshooting at the bottom.
[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)

---

### Post by Tumpster on 2007-08-07
I've had it lock up during gameplay as I accidently hit the take a screenshot button, usually it locks as I'm hitting apply when I fix my settings around on the main screen. It's locked up once during loading onto a server for CS 1.6. So it's pretty random it would seem....ideas?

---

### Post by Rocket2DMn on 2007-08-07
I've always had my cs lock up if I try to minimize the game or get back to the desktop.  If none of the troubleshooting options work on that link I gave above, I'm pretty much out of ideas.  The only other option would be to try with different video drivers (like the restricted ones if you're using the open source ones, or vice versa).  I use the open source ATI driver.

---

### Post by Tumpster on 2007-08-07
how can i tell i'm using open or closed source drivers? ive been downloading the ones off of ati's website.

---

### Post by Rocket2DMn on 2007-08-07
Ah, yes I wouldn't recommend using ATI's from their website (these are closed source).  If you do need restricted drivers, I would suggest using the repos to get them.  

First off, what video card do you have?  Please post the output of ```
lspci
```


The guide I followed to setup Beryl (now it's Compiz-Fusion) starts off by removing the restricted ATI driver and setting up the open source one, so if you follow the first page of this guide, it will help you to do so.  [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Obviously, don't proceed to install Beryl.

---

### Post by Tumpster on 2007-08-07
craig@craig-desktop:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
0000:01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:01:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:01:09.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d1)
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 15)
0000:05:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
0000:05:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
craig@craig-desktop:~$

---

### Post by Rocket2DMn on 2007-08-07
Yeah, I would go ahead with the driver setup I sent you in my previous post (the Beryl one for the open source drivers).  With that you should hopefully have better luck with your video when playing.  Let me know how it goes.

---

### Post by Tumpster on 2007-08-07
I've followed that step by step but everytime I make the adjustments and restart X server, it fails....I have to dpkg-reconfiguer to get my interface running again. I guess I'm stuck with the closed drivers..... :(

Unless you have any ideas of course?

---

### Post by Rocket2DMn on 2007-08-07
OK, then I suggest following this guide for getting the restricted drivers (linked for Dapper) - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c3f28515df1775ec5e62e78fd6c0f8f54e5f9302](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c3f28515df1775ec5e62e78fd6c0f8f54e5f9302)
You might have better luck if you upgraded to Feisty, but that's another story for another thread.

---

### Post by Tumpster on 2007-08-07
But I have a rock solid edition of dapper running right now, I don't wanna screw with that at all......I mean what would an upgrade to fiesty give me?

---

### Post by Rocket2DMn on 2007-08-07
I never used Dapper, so I can't speak for that, it was only an idea.
Since ATI support in linux is minimal, we're just getting the shaft.  I was fortunate enough to get my card to mostly work, but even then I still can't use my dual monitor or S-video.
I'm pretty much out of ideas unless you have any new information to offer.  Sorry, dude.

---

### Post by Tumpster on 2007-08-07
Thats alright man, you've helped me immensly. My plan from here on out is to purchase a new graphics card, would you be surprised if I tell you it's going to be a nvidia card! :) 
This one: [http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=322834](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=322834)
is a step up from what I have and does everything I need it to and dosen't break the bank. Plus it's linux friendly!! :)

---

### Post by Rocket2DMn on 2007-08-07
> **Tumpster said:**
> Thats alright man, you've helped me immensly. My plan from here on out is to purchase a new graphics card, would you be surprised if I tell you it's going to be a nvidia card! :) 
This one: [http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=322834](http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=322834)
is a step up from what I have and does everything I need it to and dosen't break the bank. Plus it's linux friendly!! :)

Very cool man, wish I could upgrade my laptop video card so easily.  Good luck!

---

### Post by Tumpster on 2007-08-07
So for some reason now, UT2004 and Q3 won't run for me, they get to the part where their suppose to kick over to the black screen to run but they go right back to the desktop. Any ideas?

---

### Post by Rocket2DMn on 2007-08-07
Just go back to using the drivers you had before.  If that doesn't work, then something else got screwed up.

---

### Post by Tumpster on 2007-08-07
This was going before I tried new drivers, since yesterday....

---

### Post by Rocket2DMn on 2007-08-07
Honestly, I don't really know.  If you're trying to use direct3d, that chances are that won't work since directx is a microsoft thing.  You might want to start a new thread about that and mention what you have tried, otherwise just wait until your new video card gets here since you'll have to set it up then, too.

---

