---
title: "first-gen macbook - no sound recording"
date: 2007-05-10
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-10
Has anyone been able to record anything on the first-gen macbooks?

I have tinkered endlessly with all the sound controls and have never been able to record from any source.

I'm not posting logs and settings yet, I just want to know if someone has done it.

---

### Post by ronocdh on 2007-05-10
Actually, I don't know whether it's been done on any of the laptops; I'd like to hear about *anyone's* experience with recording. I'm pleased that Feisty automatically disables my speakers when I plug in headphones now, although it's not smart enough to change what the F-volume keys affect. (They only change speaker volume and so are useless with headphones plugged in, unless I change the setting in the sound panel. But then I'd have to change back once I unplug the headphones. Please post if you have a quick fix for this!)

I'll test my recording tonight. I'd like to see the success rates with recording via built-in mic or the line-in jack. Man, I really should have thought out that survey better... :oops:

---

### Post by Zelut on 2007-05-10
I have been testing and checking launchpad for issues with the microphone all day.  I can not get anything to record on any input so far...

...and I have the same issue with the volume keys that you have. A fix for that would also be nice.

---

### Post by benanzo on 2007-05-11
I can officially record (barely) with the isight mic using only audacity...sound recorder doesn't do anything.

---

### Post by nicfagn on 2007-05-11
> **benanzo said:**
> I can officially record (barely) with the isight mic using only audacity...sound recorder doesn't do anything.

I lost a lot of time because of bugs in sound recorder! :mad: 
First of all, after recording a new sound  the play button doesn't work. You have to save the sound to hear it in sound recorder, but to save the sound you can't just use the save button or menu (it gives an error).
You have to use the 'save as...' menu and after that the play button works as expected.

So I looked for a better way to see if sound recording is working and found this command:
```
arecord -vv /dev/null
```
It continuously outputs a line with the current input source level, so you can immediately see if any sound arrives from the current input source.

Running the command in one terminal window and playing with alsamixer in another, I made sound recording work on my iMac Core 2 Duo 24'' (Intel HDA, Realtek ALC885)  with alsa-driver-1.0.14rc4 recompiled from source.

If alsamixer has a device called 'Input gain', set it to the max, this should help with the recording level.

---

### Post by Zelut on 2007-05-11
Well that is good to know.  That sure would explain why sound recorder wouldn't play back *anything* on any input from any device.  That is time I'll never get back.

I'll try your method and see what my results are..

---

### Post by Zelut on 2007-05-11
sure enough, I run the suggested command:

arecord -vv /dev/null

and the bar starts jumping all around.  I guess we can stop troubleshooting them so much and start troubleshooting why sound recorder is such a POS.

---

### Post by ronocdh on 2007-05-13
> **Zelut said:**
> sure enough, I run the suggested command:

arecord -vv /dev/null

and the bar starts jumping all around.  I guess we can stop troubleshooting them so much and start troubleshooting why sound recorder is such a POS.
=/ Why use Sound Recorder over Audacity ever?

---

### Post by DucentiVigintiDuo on 2007-05-29
I've been tinkering with the sound settings for days now, when I should've just searched for this thread right away. Lots of lost time right there.

Now I can hear the recording after saving the file in sound recorder and I can see the bar jumping, but that's pretty much it.

Audacity doesn't work for some reason, and when I start the JACK server to try out Ardour, it does some clicky/crackling distorted sounds if it starts, but most of the time it'll just say I can't connect to the JACK server as a client.

Can anyone tell me what they think might be wrong?
I could really use some help as recording's tUOTEhe only thing that's keeping me from considering Ubuntu perfect at the moment, and I need it gravely.
I'm running Ubuntu Studio, the low-latency kernel.

EDIT: Here is the JACK error output.
EDIT2: No, it's not. I realized it wouldn't start because I was running XMMS, stupid me. However the annoying rapid clicking/scratching still goes on, and even though now recording in Ardour works it's terrible and skippy/clicky as well. Help, anyone?

---

### Post by jasonparekh on 2007-06-02
Hey guys,

To be able to record, you need to toggle the Input Source to Line and then back to Mic.  Run this in the shell:

amixer sset 'Input Source' 'Line'
amixer sset 'Input Source' 'Mic'

(think you'll need alsa-utils (could be named something else) package installed)

This should let you record in any apps..

Here's the info from my blog (really old post, so has a lot of info that's been included into the kernel):
[http://www.jasonparekh.com/linux-on-macbook/#microphone]("http://www.jasonparekh.com/linux-on-macbook/#microphone")

jason

---

