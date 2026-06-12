---
title: "I need an &quot;works out of the box&quot; 5.1 sound card under $100 for Fiesty"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Jump on 2007-05-18
Can someone help me find a sound card under $100 that supports 5.1 surround out of the box with Feisty? It would be much appreciated!

---

### Post by theicyj on 2007-05-18
I'm using a Soundblaster 24 bit pci card (Live! 7.1 24bit [SB0410]).  Works out-of-the-box with lots of option in the volume control panel.  It is capable of 7.1, 6.1, and 5.1 audio.  It runs at about $25 (US) or so.

---

### Post by esoterica on 2007-05-18
Probably not what your looking for, sounds like your wanting something a little more hi end, but the onboard Intel 82801G sound card built into my laptop (AC 97 Controller I think) worked just out of the box in my Ubuntu install with no need to do anything to get it working. Since it's on a laptop I haven't tried 5:1 audio on it but the specs at the Intel web site claim it supports up to 6 channels and surround sound capabilities. It's pretty much a standard onboard audio on many Intel mother boards so you wouldn't be paying anything extra for it.

I would highly suggest staying away from anything that uses Cmedia's chip sets on it though, I've seen plenty of documentation and avaiulable Linux drivers for their audio devices but a lot of haunted Linux users who either had little to no luck getting any of them to actually work, myself included in that list of dissatisfied Cmedia victims..

---

### Post by esoterica on 2007-05-18
Also, before laying down your cash for any audio card, do a web search on that particular one to see what kind of problems other people are reporting on it in Linux. Sometimes a given device may work fine for those who recommend it to you, but others may have had a lot of trouble with it. Since you have the luxory of picking and choosing and not being stuck with what's built into your laptop like I am you may as we'll take full advantage of that. Audio cards and Video cards seem to be trouble spots for Linux beginners, after that wireless cards seem to give some people trouble as well so these are all things you should carefully consider like your trying to do.

This may be worth your time in reviewing as well...

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by dbd on 2007-05-20
The M-audio Revolution has been highly recommended by a couple of forum people, see here:
[http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268)

It's not quite "works out of the box" since you need to install the latest version of Alsa, but other than that it looks pretty much perfect :)

---

### Post by blackspyder on 2007-05-20
my Soundblaster Audiology SE ($20 USD Available @ your local Walmart) Works w/ Feisty after a little ALSA tuning (but thats b/c I have onboard and multipule other things to take in accout for that not many people have). Also it works well with my RCA surround sound in Analog mode but if you want digital this card is not for you.

---

