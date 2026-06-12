---
title: "Need terminal command for graphics card identification"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-23
My problem is I need to know what terminal command to use to find out what kind of driver to use to reconfigure xorg. I used vesa the first time and nothing is working as it should. I can't get my screen resolution back to the original setting (1024x768 is the highest available-- it used to be much higher). I was messing around last night trying to install compiz-fusion and after following the how to, when trying to start the program I was advised my system could not run it. After restart my res was all messed up, and I can't even get to the X in the upper right of the screen to close programs or move any of my open windows now. Guess I messed up big time. I did the sudo dpkg-reconfigure phigh thing with no change . Any help on this (didn't want to have to do a re-install if possible). The problem is on my Gateway 5012 Media Center comp--dual boot xp and fiesty--Pent D 1gig--250 gig SATA hd. Just need to find out what kind of video card the machine has. Thanks for the help.

---

### Post by xSauronx on 2007-07-23
lspci | grep VGA

may do it, or jus ttry

lspci

and take a look, the output shouldnt be long, and will be easy enough to understand. 

this:

[http://support.gateway.com/s/PC/R/GTModels/5394/5394sp3.shtml]("http://support.gateway.com/s/PC/R/GTModels/5394/5394sp3.shtml")

suggests it would be an intel gma 900. i havent installed drivers for it before, but id start by searching the forums here for it, i should think it would be easy enough, given their good graphics driver support

---

### Post by RomeReactor on 2007-07-23
Hi. For a more detailed output, you can also try:
```
sudo lshw -class display
```

---

### Post by jerrynewt on 2007-07-23
Thanks for the quick reply guys, but decided to go ahead and do a fresh install from the live cd. That is what I love about linux--fresh install and an hour and a half later it's like nothing ever happened. Time to shut the "Windows" and lock the "Gates". thanks again- this forum is the best!!!

---

