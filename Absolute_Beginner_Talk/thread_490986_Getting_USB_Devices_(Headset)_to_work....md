---
title: "Getting USB Devices (Headset) to work..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-03
I am not sure if this is all USB devices, or just my headset...

I have a Logitech USB headset that I am trying to get functioning...

I have gone into System > Preferences > Sound and set all the devices to USB Headset.

The test sounds come out of the headset, but YouTube and Google videos have the sound out of the internal PC speakers.

Is this a driver issue, or does it have something to do with Flash driven products?

Any clues as how to fix this?

---

### Post by paradoc on 2007-07-03
Sounds as if it's working, may only be a set-up problem?
If it's a self-powered unit like USB speakers, try this fix
> With System>preferences>sound>USB Audio...the 'test' is ok--- leave settings as, and Close.
Ubuntu Sax.ogg (in examples), now plays from both HD installation and (if setup the same) on liveCD in Feisty
If left on Autodetect though,(in sound preferences), the USB speakers will be silent when the main speakers are turned off.
      ......could be as simple as this!

---

### Post by TheBlackWizard on 2007-07-03
What fix? 

Huh? 

Sorry, but that sounds like three totally unrelated statements...

You are dealing with a newbie here...

I already did go change the sound setting to  USB Audio, and the test button does put the sound into the headphones.

But when I go to youtube, or the such, it plays through the speakers.

---

### Post by paradoc on 2007-07-03
I just thought that you had left it on 'Autodetect' instead of USB audio, and that this would account for the unexpected behaviour...........other than that, I don't know (I'm a newbie too, you know!

---

### Post by -ben- on 2007-07-09
!!!

I have exactly the same problem, Logitech USB headphones.

I have set everything to USB headphones in both the setup and sound controller. Some tings work (test sounds, mp3 player and skype) but OpenArena and even VLC media player have no sound :(

Somebody save us! :D

---

### Post by SQuark on 2007-07-09
I had the same problem with my USB speakers, and after much searching found this solution:
```
asoundconf list
```
your USB headset/speakers should be in there (mine were just called "Audio"), now:
```
asoundconf set-default-card Audio
```
replace "Audio" with whatever your device is called. Now reboot and you're done.

---

### Post by Station on 2008-01-25
is there an easier way to switch from the headset to pc speakers. 

I am having the same problem, cept my pc speakers work all the time and my headset only works with the beeping test option. Is is possible to switch between, turn on and off either the headset or the pc speakers?

---

