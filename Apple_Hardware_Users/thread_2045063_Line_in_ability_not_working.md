---
title: "Line in ability not working"
date: 2012-08-20
forum: Apple Hardware Users
---

### Post by rmcellig on 2012-08-20
I have a radio hooked up to my iMac through the audio in/out ports on my iMac. It works great on the Mac side as far as recording shows to my iMac. On the Mac side I go into the Sound prefs window, click on the Input tab and see the sound bar moving indicating that it can see the sound coming from the radio. 

When I boot into my Linux partition, and go into the sound prefs, there is no audio activity like there is on the Mac side. What do I need to get this working?

At the moment I have Zorin 6 installed but I can tell you that I had the same issue with Puppy Linux installed, Ubunti 11.04, 11.10 and other previous versions of Ubuntu.

What info do you need in order for me to solve this issue?

My iMac is 24" circa end of 2006.

On the Mac side, if I install Linux into Virtualbox, I can record from the Line in option with no problems.

---

### Post by wheeze on 2012-08-20
I just sorted a similar problem I was having hearing input from line-in while I was recording. I'm using straight ALSA with no Pulseaudio, so this may not work for you.

Go into the mixer for your sound card and make sure on the Playback tab that the Line-In is not muted and is turned up. This allows you to hear what's coming in through that port.

---

### Post by rmcellig on 2012-08-22
My Line in volume is up. I don't see any sound activity at all. Could this be a driver issue?

Is there anyone out there who has an iMac and who is able to use the Line In option without issues? I'm sure there must be a way to get this working.

My iMac is a 24" from late 2006
My radio is an Aiwa 945 that has audio in/out jacks allowing me to hook it up to my iMac through the Audio in/out ports using RCA cables. Works great on the Mac side. I can record shows from the radio as well as use the radio for my external speakers (this also works fine in Linux). It's just the ability to record audio from my radio that is the problem and I need this ability to record my radio shows.

I looked at this guide but could not find anything relating to my problem.

[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

