---
title: "Installing nVidia Drivers"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Escanor Tanthul on 2007-03-04
Hey all,

Earlier in a post I made I asked about how to install nVidia drivers for my video card:

[http://www.ubuntuforums.org/showthread.php?t=375633](http://www.ubuntuforums.org/showthread.php?t=375633)

A helpful soul directed me to this link in the ubuntuwiki:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I started to follow the directions but how do I figure out what "Linux-Image" I have installed? They give the example of "linux-restricted-modules-amd64-k8" Where do I find that information? If it helps I'm running on a 1.8Ghz Celeron Processor. My video card is supported on the "list of cards" so I know I need to get the nvidia-glx drivers

Finding my linux image is the hurdle I need to get past.

Any help is appreciated :)

--Escanor

---

### Post by mrmonday on 2007-03-04
I will solve your problem the easy way... just use [envy]("http://www.albertomilone.com/nvidia_scripts1.html").

It will do everything automatically for you to save messing around :D

EDIT: You need to have all the repositories enabled, ask if you aren't sure:)

---

### Post by Escanor Tanthul on 2007-03-04
Yeah, I installed the package and went to the terminal and ran envy. I selected the first option to install the nVidia Drivers and it flashed the screen and asked me to login again, Happened all in a matter of seconds so I don't think it worked quite right.

Any Ideas?

EDIT: I figured it out, I didn't read far enough down the envy page to read that I had to run the program without the xserver running. I logged out, killed it, and ran envy and it did it's thing. I appear to now have the appropriate nVidia drivers installed as I can play "Chromium" without any issues. It's a game we found in class oneday, pretty cool shooter.

Thx MrMonday!

---

### Post by mrmonday on 2007-03-04
Glad to help :D envy is also good if you loose your GUI for no particular reason... Just uninstall then reinstall, it makes life so much simpler :D

---

### Post by mrbungle on 2007-03-04
i love envy :guitar:

---

