---
title: "Total system lag. Everything is slow?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-06-04
Ok...cant really pinpoint when this started.

But lately everything has been really really slow. 

I've had ubuntu running on this machine for a good couple months. No big problems to speak of.

I cant really think of anything i could have done to cause this.

But everything just lags horribley....

For example. 

1-I open firefox. It sits for a bit, then the frame pops up, then some menu, etc....after a couple literal minutes all of it loads.

2-The screensaver. It will come on, but all animation will be unbearable slow. 
Move the mouse to get off screensaver mode....then the desktop takes time to come up. Same as before. First the frame, then the menu......over the course of a couple minutes everything is up.

Switching work spaces is the same


What the hell did i do? What can i do to fix this?

Everything had been running really nice and smooth before.

I have tried just restarting the computer. Nothing changes.

---

### Post by CloudyHaze on 2006-06-05
come on....anyone????

---

### Post by joshrobinson on 2006-06-05
[QUOTE=CloudyHaze]come on....anyone????[/QUOTE]

although you might not like the idea of it, or someone else might have a better solution.. this is about the time i would do a clean install.. but hopefully someone else can point you in the right direction to save you the hassle

---

### Post by richbarna on 2006-06-05
Couple of months? Dapper or Breezy ?
Ok first thing, Can you post some system specs ?
Graphics card etc.
Have you installed anything that is graphics related or service dependent? anything usb plugged in ?
Does it stop if you unplug your router/modem?

---

### Post by CloudyHaze on 2006-06-05
Ok..... 

AMD Semperon processor. 
NVidia GEForce2 Graphics card.
130GB Hard Drive.
1GB Ram.


I was doing some video editiing via Kino a week back. Which was quite resource heavy. 

Have been watching a bunch of different movies/videos.

Also been having problems with getting an external USB Hard Drive working(may still be plugged in if thats an issue?)

I've been contemplating upgrading to Dapper,...but first I NEED to get the external working so i can back up all the video stuff ive been doing.

When I view the current running processes, nothing out of the ordinary is going.

---

### Post by joshrobinson on 2006-06-05
can you post the output of the following command

```
free
```

when you plug in your external drive does it appear in system >administration >disks

what file system is it? fat32?

---

### Post by CloudyHaze on 2006-06-05
im at work now....so the machine is not with me.


when i plug in the external it does not appear in system>admin>disk

and yes it FAT32 formated i think

---

### Post by richbarna on 2006-06-05
The first thing I would look at is the hardware.
Make sure nothing is overheating (I know it sounds stupid) but people don't see a blocked fan until the processor melts.
Maybe there are bad sectors on the hard drive (how old is it?)
You may not notice them until you've filled it with video files.

Other things to try :-
Lower the screen refresh rate to 60 if it is higher.
Try another desktop environment to see if it is that.
Create a new user and then login to see if there is any change.
Once I managed to completely bork my desktop but my wife's was ok.
Check the xorg.config file for changes (driver settings).
Update the graphics card driver.

Lastly are you on a network, do you use wireless ?
Is there an unwanted guest milking your internet ?

---

