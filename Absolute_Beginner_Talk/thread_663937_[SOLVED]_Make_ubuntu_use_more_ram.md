---
title: "[SOLVED] Make ubuntu use more ram"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by linuxrock on 2008-01-10
I don'thave any problem with my ubuntu but my pc has 3 gig of ram and he only using average of 500 mb of ram, is there a way to make ubuntu using more ram for more performance? And by the way thanks to everybody for there great support on this forum!

---

### Post by SunnyRabbiera on 2008-01-10
so do you want it to be a ram hog like windows or something?
overload it with usesless toys and effects then ;)

---

### Post by phenest on 2008-01-10
Why don't you take some RAM out, instead? Problem solved.

---

### Post by Joeb454 on 2008-01-10
Run loads of fancy Compiz-Fusion effects, that should push your RAM up by ~100-200Mb if your lucky :)

Or you could just open EVERY app that you have installed :)

---

### Post by bodhi.zazen on 2008-01-10
> **linuxrock said:**
> I don'thave any problem with my ubuntu but my pc has 3 gig of ram and he only using average of 500 mb of ram, is there a way to make ubuntu using more ram for more performance? And by the way thanks to everybody for there great support on this forum!

Linux does not use RAM in the same way (as windows) and it sounds as if from your average usage you have 2.5 Gb of ram too much.

If you fill your RAM you will start to use swap.

So, when trying to optimize performance, you can tell you may benefit from more RAM if you are using swap.

In your case your performance is not limited by RAM, but by something else.

It is a misconception that just because you have more RAM your system will be faster. This is only rue if you are running out of RAM.

You can check these links : Firefox Speed up : [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

	[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

[http://ubuntuforums.org/showthread.php?t=459101](http://ubuntuforums.org/showthread.php?t=459101)

---

### Post by PinkFloyd102489 on 2008-01-10
Do this, it'll force Ubuntu to use more RAM instead of swap.


```
sudo nano /etc/sysct.conf
```

Add a line at the bottom that says:

```
#Swappiness
vm.swappiness=0
```


Hit Ctrl-O to save and then Ctrl-X to exit then restart your system.

---

### Post by wolfen69 on 2008-01-10
ubuntu will only use ram as needed. if you start opening many apps, it will load into ram. nothing to worry about.

---

### Post by linuxrock on 2008-01-10
Thanks a lot. It was just pissing me off because i just pay a lot for it because of vista and now its mostly useless too have so much ram.I should have known linux sooner it will have save me a lot of money.:(

---

### Post by Niniel on 2008-01-10
Lucky you! Now your apps will have more RAM and your swap partition will surely die of boredom. 
It's not a problem, it's a feature. :)

---

### Post by Whiffle on 2008-01-10
You could always install preload as well... 

[http://packages.ubuntu.com/edgy/misc/preload](http://packages.ubuntu.com/edgy/misc/preload)

---

### Post by nowshining on 2008-01-10
linux uses RAM as cache also..

1.) The kernel takes up some ram - about 8mb that's why u may see a little less available for apps.  The kernel is always in RAM.

2.)U can add system monitor apps to the taskbar if u'd like anywhere to monitor ram, network, etc.., right click to configure it and add more than just thing - which I think is CPU by default.

3.)The linux kernel should use up all RAM already  - the rest only being cache that can be freed up anytime an application needs it. :)

oh and that vm swappiness is okay but u'll still prob. get a few kilobytes in swap, i know I have even tho there is a lot of free RAM for apps.

---

