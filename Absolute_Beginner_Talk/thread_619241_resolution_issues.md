---
title: "resolution issues"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by watchinthewhels on 2007-11-21
Hi guys, im new to linux and im having trouble getting the display configured.

I am using an nvidia card (with the propriatory drivers) and it was working fine for a while with all the resolutions I needed. Unfortunatly I decided to fiddle, that was a mistake. I set the res to something my monitor couldnt display so when I tried to login it would give me an out of range message.

So I booted to the command line and edited the xorg.conf file manualy. I deleted all the resolutions my monitor couldnt display and it still wouldnt boot, so i cut the list down to 800x600 and lower. This eventaly let me into the GUI. 

Unfortunalty I now dont know how to get my resolutions back. I have found files in the X11 directory called xorg.conf.1 to xorg.conf.11 all with different settings which all seem related to my monitor (correct name of device anyway) So i have tried replacing the default with thiose from the command line but every time I get the same out of range message. 

I have tried rescanning the file using the auto-config utility that xorg provides but that still gives me the same issue. Im really not sure how best to go about fixing this, is there any way for scrapping all data that xorg has and then re-scanning as if it was a fresh build. Or is there a better way than that.

Im really hoping you can help, but bear in mind i really am a newbie to this, and despite struggling through several commands i really am stabbing in the dark for a lot of it.

Thanks in advance for any help.

---

### Post by Dr Small on 2007-11-21
Try this in a terminal (CTRL + ALT + 1):
```
sudo dpkg-reconfigure xserver-xorg
```

---

