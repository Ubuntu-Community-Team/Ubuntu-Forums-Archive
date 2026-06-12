---
title: "Audacity error"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-12-05
I'm using Ubuntu Studio 7.10 and i'm recording though the usb with my Behringer U-CONTROL UCA200 and when i try and do another track in the recording it comes up with the bellow error.

> Error while opening sound device. Please check the input device settings and the project sample rate.

Could any one help me with this please.

---

### Post by ArtInvent on 2007-12-05
I'm confused. Are you able to record the first track or any track with the Behringer. Which v. of Audacity are you using? Are you able to record from this unit with Sound Recorder? 

Also note that Audacity uses OSS which is the older Linux sound interface scheme. What is the selected device in the Preferences | Audio I/O section? 

I remember having similar difficulties with a USB sound adapter but I can't remember exactly how I resolved it. My sound only works in Audacity using OSS. The default these days is to use ALSA.  I remember something about having to install a package called **alsa-oss** which is something to look into if you haven't.

---

### Post by ArtInvent on 2007-12-05
I don't know if you've seen this thread but it recounts some of my and other's problems/solutions with Audacity and aoss etc.

[http://ubuntuforums.org/showthread.php?t=416166]("http://ubuntuforums.org/showthread.php?t=416166")

---

### Post by reesy on 2007-12-06
Yes I am able to record the first track but then then when i hit record for the next track it comes up with that error. The version of Audacity I'm using is Audacity ® 1.3.3-beta. I tired opening sound recorder and it gives an error > Your audio capture settings are invalid. Please correct them in the Multimedia settings.
The playback device in Preferences | Audio I/O section is OSS: dev/dsp and the recording device is ALSA:USB Audio CODEC: USB Audio (hw:1,0)

---

### Post by ArtInvent on 2007-12-06
For the record device you are using ALSA. My understanding is that Audacity has issues with ALSA, though 1.3.x should be better than the 'stable' 1.2 series.

Is there a choice in the recording device dropdown for using OSS with the USB device? Have you changed these setting's and experimented with the different choices? Have you tried installing alsa-oss? What sample rates and bit depth are you using. Try switching to 44kHz-16b or lower if you are using higher formats and see what happens.

What worked for me was to install alsa-oss, then I would start audacity with the command line **aoss audacity**. After I did this once, I was able to start audacity normally without the aoss command and it seemed to work. (That part is mysterious.)

Here is a somewhat outdated but detailed explanation of issues with USB devices in Audacity: 
[http://audacityteam.org/wiki/index.php?title=USB_mic_on_Linux]("http://audacityteam.org/wiki/index.php?title=USB_mic_on_Linux")

As with any software/hardware difficulties, you need to try and change all the settings that you can change and see what happens.

As an aside, I have stuck with Feisty because everything works, even though I would of course much rather move to the latest Gutsy for all the nice features.  But when you have odd audio hardware and 'beta' software like Audacity, new versions of things like the OS itself can break things. I will probably give 8.04 a go since it's a long term support version. Unfortunately multi-media in Linux is still not mature enough to the point where you can just make a major change like that and expect everything to work. My approach when a new v. of Ubuntu comes out is to NOT just upgrade my existing install. I get a second hard drive and install the new version to that drive, install ALL of my hardware and apps and make sure it all works. If not, I can always just uplug the drive and go back to the previous system. Hard drives are pretty cheap these days.

---

### Post by reesy on 2007-12-06
I've got it working now.I had to set the output device to the the Usb, through the Usb then I connect the usb output to my other mixer and that mixer to the amp and i had sound playing back and it would let me record more tracks :D.

---

