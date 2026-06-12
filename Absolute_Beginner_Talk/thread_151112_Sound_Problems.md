---
title: "Sound Problems"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by gaberade on 2006-03-27
My sound works and all, but for some reason I can't adjust the volume. Even when I set it to mute, it'll play everything at max volume.

I'm running a Dell Inspirion 9100...
Onboard audio is Sigmatel STAC 9750 AC97

Anyone care to help?

---

### Post by meborc on 2006-03-27
right-click on the volume button and see if the correct device is selected... if you have many devices (motherboard chip + soundcard) it is possible, that you have been trying to set the volume of one when using the other...

just a thought to try out ;)

EDIT: just came to my mind that you only have onboard sound... well... it was worth the try :D

---

### Post by gaberade on 2006-03-27
[QUOTE=meborc]right-click on the volume button and see if the correct device is selected... if you have many devices (motherboard chip + soundcard) it is possible, that you have been trying to set the volume of one when using the other...

just a thought to try out ;)

EDIT: just came to my mind that you only have onboard sound... well... it was worth the try :D[/QUOTE]

It is on board sound, but there's two choices there when I go to preferences. There's SigmaTel STAC9750,51 (OSS Mixer) and then there's Intel ICH5 (Alsa Mixer). When I switch over to SigmaTel and I have the preference window open with the Volume Control window I can adjust the volume fine with the sliders in the VC window. (It says PCM btw). But my media buttons and when I single click on the audio button to bring up the little slider seem to be controlling the Alsa Mixer which is apparently not affecting the volume for what ever reason.

---

### Post by meborc on 2006-03-27
run alsamixer in terminal and change the device there... i'm not at my ubuntu so i can't check it right now, but as i remember there are 3 places to set the device... one is the volume button you tried... the second is alsamixer and the third and probably the most important (or least) is from the menu system > preferences > sound ... or smth... try to play around with different devices and settings (alsa/oss) ... also be aware that different programs use different settings (alsa/oss again) by default.. and you might need to change them...

there was a thread concerning playing multiple sounds at the same time... you might want to search for it and read that one... sorry for not being able to help you... just to guide you ;)

---

### Post by rockstar on 2008-03-24
So, I figured out how to sepporate my Sub from My front speakers with this thread.  This might fix your volume issues.  I couldn't get the sound to mute unless I muter PCM directly because of the Master and Mono Master sound setup.

[http://ubuntuforums.org/showthread.php?p=4575194#post4575194](http://ubuntuforums.org/showthread.php?p=4575194#post4575194)

But why do you have both the Alsa mixer and the OSS mixer?

---

