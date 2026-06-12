---
title: "Master Volume Does Squat"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by HokeyFry on 2006-11-27
yeah umm... the master volume control doesnt work. I do have sound, and I can control the volume of most things by changing the PCM volume level, but i would really like to know why changing master volume does nothing.

---

### Post by bodhi.zazen on 2006-11-27
> **HokeyFry said:**
> yeah umm... the master volume control doesnt work. I do have sound, and I can control the volume of most things by changing the PCM volume level, but i would really like to know why changing master volume does nothing.

Not to ask the obvious, but do you have more then one sound card?

---

### Post by vtel57 on 2006-11-27
If your mobo has onboard audio and you have an audio card installed also, then Ubuntu won't know which sound device to default to. You can choose which device is the proper one by opening the volume control panel and clicking on File at the upper left, then choose Device. If there are more than one listed, choose the one you want to use as default.

Luck!

---

### Post by HokeyFry on 2006-11-27
thanks ill try that once i get home from school

---

### Post by HokeyFry on 2006-11-27
umm funny story... it doesnt matter which one i choose. if it helps though here are the choices:

Intel ICH5 (Alsa mixer)
Analog Devices AD1981D (OSS Mixer)

its currently set to intel

---

### Post by vtel57 on 2006-11-27
Leave the ALSA mixer as the default. Go to Main --> System --> Preferences --> Sound --> Sound tab --> make sure the default down at the bottom is the same as the default in your volume panel.

---

### Post by Ocxic on 2006-11-27
I've had this same problem scince breezy, I havn't tested it with my onboard audio, but it does nothing for my usb stereo. no biggie, but still one wonders.
(muting works)

---

### Post by HokeyFry on 2006-11-28
yeah the Intel one is set as the default.

however that is the only choice, the analog device isnt available as a choice

---

### Post by kingbilly on 2006-11-28
When you right click on your volume control icon and choose properties, is the master(or volume) set to be controlled?  I had overlooked that and didn't have control for a while.  Turned out the default control for the knob was for the mic. Its probably deeper then that but i'm just making sure.

---

### Post by HokeyFry on 2006-11-29
hmm i havent tried that yet ill try that once i get home


if its that easy though i think i will shoot myself lol

---

### Post by mun3kh on 2006-12-01
I still have this problem, and it appears that I have the same Intel onboard sound card (if that's not a contradiction in terms)

What gives? Is there any way I can run the volume control from a terminal, to get error output from sliding it up or down?

---

### Post by DougieFresh4U on 2006-12-01
I hope that there is better luck in this thread as I have been posting the issue in the "General Help" section for over a week, and no responses. I have the same Intel and same exact issue. Sorry for ranting on in your thread :p **Dougie**

---

### Post by HokeyFry on 2006-12-01
i dont know but if you right click the volume control and view properties (assuming there is a selection for that) you might be able to see the terminal command... i never thought of that ill try it and post whatever error there is if there even is an error

---

### Post by HokeyFry on 2006-12-04
i did find a temporary workaround. when you right click the volume icon, click proterties, and select PCM from the menu. this makes the slider control the PCM volume instead of the master volume.

thanks to kingblly for pointing out the properties menu, though i wuold like to be able to control the master volume. what IS the terminal command for the volume window so i can see if theres an error when i slide the bar?

---

### Post by stephentastic on 2006-12-11
[FONT=Georgia][FONT=Courier New][SIZE=3]I'm not sure if you have already tried this, but I was having the same problem and this worked for me (sorry if this is not the trouble you have been having):

Right Click on the Volume Icon on the panel and select Preferences

Make sure that the device that appears in the drop down list is the sound card/device used by Ubuntu

Select "Master" from the list below.
[/SIZE][/FONT]    
[SIZE=3] That's what worked for me at any rate.
I'm 3 days in on the linux thing, so forgive me if this isn't what you were looking for!
[/SIZE] 
[/FONT]

---

