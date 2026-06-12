---
title: "M2N DH AD1988 Sound isue"
date: 2012-01-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Mike_Wilkinson on 2012-01-04
Hi, please bear with me but I'm a bit of a Noob with Linux.

I'm having an issue with trying to get surround sound working correctly on my desktop.

I'm running a fresh install of Lucid and I@ve upgraded ALSA to  v1.0.24. 

I've established that the onboard sound is via an AD1988 chip and that it is handled by a MCP61 Audio controller.

I've already edited Alsa-base.conf to include the 3stack-dig option which enabled the correct sliders in Alsamixer and also allowed Pulseaudio to select Analog 5.1. I have general sound with the front left and right channels being output over all the speakers - not a problem for music.

However, when running the speaker test I only here front left and front right, more bizarre is that front left sounds from the both left speaker and centre and front right sounds from both right speakers and the sub?

Playing around with alsamixer I've found that I can silence each set of speakers, but still only here front left and front right. It would appear that the front speaker output is being written to all three jack outputs and the rear channels and sub/centre are not outputting anywhere?

Any help would be much appreciated. Mike:confused:

---

### Post by lidex on 2012-01-04
> **Mike_Wilkinson said:**
> Hi, please bear with me but I'm a bit of a Noob with Linux.

I'm having an issue with trying to get surround sound working correctly on my desktop.

I'm running a fresh install of Lucid and I@ve upgraded ALSA to  v1.0.24. 

I've established that the onboard sound is via an AD1988 chip and that it is handled by a MCP61 Audio controller.

I've already edited Alsa-base.conf to include the 3stack-dig option which enabled the correct sliders in Alsamixer and also allowed Pulseaudio to select Analog 5.1. I have general sound with the front left and right channels being output over all the speakers - not a problem for music.

However, when running the speaker test I only here front left and front right, more bizarre is that front left sounds from the both left speaker and centre and front right sounds from both right speakers and the sub?

Playing around with alsamixer I've found that I can silence each set of speakers, but still only here front left and front right. It would appear that the front speaker output is being written to all three jack outputs and the rear channels and sub/centre are not outputting anywhere?

Any help would be much appreciated. Mike:confused:

A couple of resources here:
[http://www.halfgaar.net/surround-sound-in-linux](http://www.halfgaar.net/surround-sound-in-linux)
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by Mike_Wilkinson on 2012-01-05
Well I have had a little play and still can't get an individual output to the rear and centre/sub speaker jacks. The system appears to only see two output channels and puts them across all three jacks. 

The best I've been able to do is to create a semi-surround system by rerouting the channels in a new PCM.
Basically I am taking the surround input channels and mapping to the two outputs

So 
Channel 0 goes to Channel 0 - (Front left -plays on front\rear left and centre)
Channel 1 goes to Channel 1 - (Front Right - plays on front\rear right and sub)
Channel 2 goes to Channel 0 - (Rear Left - Plays on front\rear left and centre)
Channel 3 goes to Channel 1 - (Rear Right - Plays on front\rear right and sub)
Channel 4 goes to Channel 1 and 0 (Centre Plays on all)
Channel 5 goes to Channel 1 and 0 (Sub plays on all)

a further messing around with gains and I essential get each channel biased to the speaker I want with the exception of the rear pair. So I have Front\Rear Left, Centre, Front\Rear Right and a Sub.

Not perfect but will have to do for now till I can work out why I'm not getting output mapped to the correct jacks on the Mobo.

Mike:)

---

