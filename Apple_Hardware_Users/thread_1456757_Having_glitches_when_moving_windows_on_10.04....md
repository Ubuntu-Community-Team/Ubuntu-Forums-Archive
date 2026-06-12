---
title: "Having glitches when moving windows on 10.04..."
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by jisaac on 2010-04-17
Hi guys,

I've just installed 10.04 64bit on my iMac 27" i7 and before fighting with keyboard, mouse, audio,... I'd like to share with you a strange behavior of the screen refresh speed, color depth and/or maybe a performance issue with the ATI. It's happening with all the resolutions and I don't appreciate it on OSX. The windows borders are "cut" when moving or scaling them, the login screen seems to have a low color depth (as banding issues) and it appears slowly from top to bottom of the screen... for example, when I open the synaptic and the system ask for the password, I can see a very slow fading effect to dark screen... :( 

I've made a full update then install the ATI proprietary drivers (from the ubuntu repositories). Basically I'd love to hear that my problem is a driver issue but it seems that 10.04 comes with the very last drivers from ATI.

Does someone experience such a behavior?
Does somebody know how to enhance it?

Thanks.

PS: Hope the attached "test.tar.gz" helps to understand better.

---

### Post by jisaac on 2010-04-18
Ups! I think it's a general Linux Desktop behavior. I'm able to reproduce it in my other Ubuntu box.

The defect is worst on my iMac probably because of the 27" screen dimensions.

Any comment?

---

### Post by tomalart on 2010-04-18
Hi Guys Using Ubuntu 10.04 Beta on a Sony Vaio laptop (slightly old PCG-4n7M). It was working wonderfully until this morning. After updating and upgrading the login screen images gave broken image icons, then on logging in UI was replaced with just the cmd shell. All menus are gone. 
  I have tried to reconfigure xserver-xorg and that doesn't work. Reinstalling doesn't either. I have tried a number of other attempts. What is weird is that I can launch graphical applications from the cmd line. such as firefox or google-chrome. and they work but the UI is simplified or broken (no resizing, closing, minimizing). 
  I am a bit lost on how to fix this error.  
  If anyone has any suggestions, please let me know


   [URL="http://www.carpartswarehouse.com/carmodels/CP6/Ford/Ranchero.html"]
[/URL]

---

### Post by linuxopjemac on 2010-04-19
lucid is still beta...don't expect everything to work yet

---

### Post by jisaac on 2010-04-21
I've reproduced very similar glitches on XP and W7 using other machines... Is it a good news for Linux Desktop?

No doubts, OSX finishes are really good!

---

### Post by jisaac on 2010-04-22
Ok. The correct name for this issue is: Screen Tearing! Sorry for the confusion. I was talking about: [http://en.wikipedia.org/wiki/Screen_tearing](http://en.wikipedia.org/wiki/Screen_tearing) :)

I've found tutorials to solve this problem configuring compiz (sync to vblank + frame rate...) but nothing. It doesn't work for me.

---

### Post by jisaac on 2010-04-29
I've managed to completely solve this issue in my other Ubuntu + NVIDIA box and at work (fedora + NVIDIA) as well.

The problem is from ATI drivers for Linux :(

I'll probably post soon a new thread with a better title and few interesting related links...

Very annoying...

---

### Post by binary10 on 2010-04-29
I think the ATI drivers have in general been a pain in 10.04. It's a real shame :(

---

### Post by cazacugmihai on 2010-04-30
Hi,

I have the same problems with my ATI card (on an iMac 27").
The symptoms:
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/305909](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/305909)
- [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Any ideas?

---

