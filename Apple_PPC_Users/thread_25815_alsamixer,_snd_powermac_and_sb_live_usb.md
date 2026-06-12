---
title: "alsamixer, snd_powermac and sb live usb"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by danns on 2005-04-10
Just upgraded to hoary.  Prior to hoary I had put on a usb soundblaster live.  I had a dickens of a time getting it to be recognized properly, well the way I wanted it, for recording purposes.  

Anyway, after upgraded to hoary I followed my same process only to note that the recording device was no longer in alsamixer.  I figured all was lost after spending about an hour trying to load and reload the modules and start and stop hotplug.  

On a lark I tried audacity and recording was not a problem, which was weird, I thought.  I rebooted with the device connected and ran alsamixer and got the same results, no capture device settings.  I did notice now that the snd_powermac is allowing me to capture audio through the line in or mic.  Did not notice this in the past, but again, no volume controls.

Both devices are working in audacity.

I took a notice that the alsamixer page had the value "playback" for view and a quick read of the man page indicated that there are three modes:  Playback, capture and all.  Well the all mode displayed the capture settings for the usb device along with the playback as it did in the past.  But trying to view the capture mode for the snd_powermac elicits the error:

    no mixer elems found

Is there a place where the default alsamixer View mode is stored?  I'm wondering why this may have changed.

---

