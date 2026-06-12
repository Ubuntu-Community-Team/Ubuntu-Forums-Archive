---
title: "Chrome not playing YouTube (Flash) Videos"
date: 2013-09-24
forum: Apple Hardware Users
---

### Post by hawkmage on 2013-09-24
I have tried installing Ubuntu as well as the latest versions of Debian, Mint Cinnamon and Fedora on a MacBookPro 6,1.  Everything works great except one annoying thing.  The Chrome browser will not play YouTube videos.  The "box" on the screen where the video is supposed to play shows but remains black as it times out on each resolution available for the video and finally gives a generic error that communication has failed.    FireFox works just fine.

I have disabled and removed the flash player lib that is built into Chrome, I have installed the flash player from Adobe, installed other third party flash players/plugins like VLC and gnash and still Chrome will not play the videos.  

Does anyone have any other ideas?

---

### Post by sanderj on 2013-09-25
Did you try Chromium?

---

### Post by enchanterchi on 2013-09-25
I am sick of fight with flash in chrome. So I choose to add extensions: "Magic Actions for YouTube" and "HTML5 Video for YouTube" which should play the video in HTML5 player with extra features. I am good with that.

---

### Post by hawkmage on 2013-09-25
I have not tried using chromium.  Chrome is built from chromium so if you start with Chrome and remove libpepflashplayer.co and add libflashplayer.so from Adobe how is that much different from adding the same lib to chromium?

Also this doesn't explain why if I install the same Linux distr and version on a Dell desk top or Virtual Box VM the exact same version of Chrome can play YouTube videos.

---

### Post by hawkmage on 2013-09-26
OK, did a bit more experimenting.  Chromium has the same symptoms and I even installed on a HP i7 laptop and again the same issue.

---

### Post by sanderj on 2013-09-27
You installed different distro's on different machines, and never Flash will work in Chrome nor Chromium, but it does work in Firefox? Weird.

What does chrome://flash/ say in Chromium?
Just plain installs, no google-login, no flash-blocker?
You're on your own LAN, not on a corporate LAN / WAN?

---

### Post by hawkmage on 2013-09-27
I have installed Debian 7.1, Ubuntu 12.04 and 13.10, Mint 15.1 and Fedora 19 on my MacBook Pro and neither Chrome or chromium will play YouTube Videos.  I have installed those same distros as a guest under VirtualBox VM on the MacBook Pro running OS X and Chrome or Chromium will play YouTube Videos.  

I have an old Dell XPS 420 with Debian 7.1 and a default install of Chrome that will play YouTube videos.  I am not going to experiment with this system because it is working.  

All of these tests are on my home network and there is nothing blocking flash or YouTube on the network/firewall.  I have the AdBlock plugin on Chrome but I have disabled it and it makes no difference.  

I will have to get back to you about the chrome://flash, since I have pulled out the drive with Linux on it.  I have used chrome://plugins and it lists the flash player I have configured.

---

### Post by hawkmage on 2013-09-30
OK, the last OS I installed on the drive was Mint and I just put it back in and took a look at the last config for flash.  Both Chromium and FireFox are using /opt/mint-flashplugin-11/libflashplayer.so and FireFox works and Chromium doesn't.  I am about install other distros as well.

---

