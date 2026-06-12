---
title: "microphone (?skype) problem"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-08-10
Hello

I've got an odd problem on skype audio. I can connect and hear the people I'm calling, but my own microphone input is routed to my own speakers, and not to the internet: so I can hear my callers, but when I reply I hear myself on my speakers and they don't hear anything.  Capture is happening, but the signal is going the wrong way. 

I've looked at the sound settings and at the skype settings but they all look (to my untrained eye) reasonably good. What am I missing? any ideas gratefully accepted.

---

### Post by arochester on 2007-08-10
You might find that the microphone is muted by default. Either access the Mixer to see what is off and waht is on, or use a program like Audacity-Sound Editor and have a play around.

---

### Post by anewguy on 2007-08-10
I'm going to assume from what you've said that you know how to get to the options in Skype, and to get to the sound options.  You'll see sound in, sound out and ringing options.  You may have to change the sound in option to another one of the listed devices.  I know mine will work some of the time (I have no idea why) set just on default device.  Most of the time I have to set it to something like one of the plughw options - in my case I have a device 0 and a device 1.  1 of them works good for sound in  and the other for sound out.  You may have to play with the devices to see if you find one that works.  Also follow the previously posted advise to be sure it's not muted - though I'm not sure how it would come out your speakers if it was.:)

---

### Post by ginestre on 2007-08-10
> **anewguy said:**
> I'm going to assume from what you've said that you know how to get to the options in Skype, and to get to the sound options.  You'll see sound in, sound out and ringing options.  You may have to change the sound in option to another one of the listed devices.  I know mine will work some of the time (I have no idea why) set just on default device.  Most of the time I have to set it to something like one of the plughw options - in my case I have a device 0 and a device 1.  1 of them works good for sound in  and the other for sound out.  You may have to play with the devices to see if you find one that works.  Also follow the previously posted advise to be sure it's not muted - though I'm not sure how it would come out your speakers if it was.:)

Thanks: but I have only one device listed, and that is chosen (obviously, as there are no others). It's the default, onboard VIA chip going thru' ALSA. But what are the plughw options you mention?

---

### Post by anewguy on 2007-08-10
Well, I have a the following under Options then Sound Devices in Skype (not the volume control/mixer) for both sound in and sound out.  This is the list I select from:

- default device
- VIA 8237 (hw:8237,0)
- VIA 8237 (plughw:8237,0)
- VIA 8237 (hw:8237,1)
- VIA 8237 (plughw:8237,1)
- VIA 82xx modem (hw:modem,0)
- VIA 82xx modem (plughw:modem,0)

If the only thing you have is "default device" with no other selections available by clicking the up/down arrow on the line, then I can't help you.:)

---

