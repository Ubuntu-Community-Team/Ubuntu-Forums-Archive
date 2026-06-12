---
title: "A few questions/problems."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by lordzargon on 2007-03-10
Installed Ubuntu 6.06.1 off the CD I got through a few weeks ago. I've been searching around the internet trying to find solutions I can understand to the problems I'm having. A lot them require the use of terminal and backing up of files which I'm a complete novice at. 
 
I managed to get my network settings correct and it connected to the internet fine first time. But everytime I boot up, its no longer connected. The settings are correct, but I have to delete out the DNS server, deactivate the wireless NIC, and go through it again, putting in the ESSID and such. The network is not secured by an authentication key, could this be the problem? Its not a huge issue, I'm pretty nifty at resetting it now, it just takes a good 5 minutes to set it all up again.

Next is what I assume to be a common issue, but I can't increase the resolution above 1024*768. I tried modifying the xorg.conf file, firstly to no avail, then I must have set the refresh rate wrong because the screen went black and I had to go into recovery mode and restore the backup. At the moment, Windows XP is runing my CRT at 1280*960 on 60Hz if that helps. 

And finally I've read about EasyCam and putting lines into various files, but I'm unsure about how exactly to go about this, so any step-by-step instructions would be greatly appreciated. Just need to install my webcam.

I'll put my hand up, I'm a complete Linux newbie. I've been using Windows for donkey's years and know pretty much every nook and cranny - but its time for a change, something new! I'm also looking into it as my younger sister is after a cheap laptop - and the amount saved from not buying XP would be huge in relative cost terms but she won't even consider it without a webcam, heh.

Thanks in advance,
Matt

---

### Post by Kateikyoushi on 2007-03-10
About the video resolution, If you have ATI or Nvidia card install the driver for it and then run this in terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by lordzargon on 2007-03-10
Alright thanks, resolution is better. For some reason the login screen runs at 1280*960, but the option isn't listed in the actual desktop resolution settings. No to worry, 1152*864 is just great :).

---

### Post by oilchangeguy on 2007-03-10
you say under xp your're using 60hz on a crt? are you sure it's a crt? or an lcd? if you've got a crt running at 60hz it's got to be killing your eyes. try setting it at 85hz.

---

### Post by lordzargon on 2007-03-10
Yeah, this heap'o'junk is CRT alright! Its fine at 60Hz, but I've increaded it anyways. 

 Can anyone enlighten my on the network/cam issues?

---

### Post by redsoftretro on 2007-03-10
Hi

Have a look at this for network issues

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Also as well as the forums I find the wiki helpful at times. There's not as much noise in there!

Cheers.

---

