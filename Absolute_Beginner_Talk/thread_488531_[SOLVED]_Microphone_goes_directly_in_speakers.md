---
title: "[SOLVED] Microphone goes directly in speakers"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by JoZ on 2007-06-30
Hi I'm really new to ubuntu: installed yesterday...
I'm having troubles with the microphone: I can control its volume in the volume control, but I can't record and my voice goes directly to the spekers...

My soundcard is a nVidia ncp51

Thanks a lot!!!!

---

### Post by tgalati4 on 2007-06-30
The first thing to do is double-click on the volume control then edit preferences and turn on everything.  You need to examine every channel and switch and start adjusting settings until you have it set up the way you want it.

---

### Post by JoZ on 2007-06-30
Need something more detailed... I spent 1 day on it, I already tried all basics adjustments... what I say in the mic still goes directly in the speakers...
Forgot to say that it looks like there Is a conflict between the microphone and the Line-in controls

---

### Post by tgalati4 on 2007-06-30
Did you find the preference tab that allows you to view all of the channels?

Post the output of:

aplay -l

Try swapping your inputs and outputs.  Modern sound chips have assignable ports, so what is labeled on the computer may not how the card is actually configured.  They tend to be correct using Windows drivers, but Linux drivers tend to either not assign them or assign them differently.

---

### Post by alienexplorers on 2007-06-30
I have the same problem so if you figure out an answer it would be great.

---

### Post by JoZ on 2007-06-30
here is the output you requested


root@ARCANGELO:~# aplay -I
aplay: playbackv:2295: You need to specify 1 files
root@ARCANGELO:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ARCANGELO:~#

---

### Post by JoZ on 2007-06-30
I found out the problem: I was working on the wrong Mixer. It has to be done in the ALSA mixer (File > Change Device)

in the first tab (Playback) the front mic or mic should be idle. 

Under recording in the capture control I muted the speakers... Now I can record and I don't my voice in the speakers. 

Thank you for your help tgalati4 ... I figure it out after enabling all the views also for the second device!

---

### Post by tgalati4 on 2007-07-01
Well, that was the basic flavor of my answer.  I'm not familar with  your hardware, but most sound cards behave the same way.  To get the extra features, you have to turn things on and play with them.  Under Windows, the drivers that you get and install take care of that and you usually get a slick GUI to make adjustments.   

Linux doesn't have these slick GUI's for the most part, but it does get the job done.  In the end, as long as you can adjust the gain, mix and mute, it doesn't matter what the GUI looks like.

I'm glad  you shared your solution.  This is how problem-solving is done in Ubuntu.  Now you are an expert in sound hardware and you can help others.

Great news indeed.

---

### Post by mytwobears on 2007-07-03
> **JoZ said:**
> I found out the problem: I was working on the wrong Mixer. It has to be done in the ALSA mixer (File > Change Device)

in the first tab (Playback) the front mic or mic should be idle. 

Under recording in the capture control I muted the speakers... Now I can record and I don't my voice in the speakers. 

Thank you for your help tgalati4 ... I figure it out after enabling all the views also for the second device!


JoZ and tgalati4, thank you both for your help.  After struggling with a non working microphone in both sound recorder and skype and following many instructions in other forum posts, this post solved my problem.  Thanks again :).

---

### Post by yurac on 2008-03-24
> **JoZ said:**
> I found out the problem: I was working on the wrong Mixer. It has to be done in the ALSA mixer (File > Change Device)

in the first tab (Playback) the front mic or mic should be idle. 

Under recording in the capture control I muted the speakers... Now I can record and I don't my voice in the speakers. 

Thank you for your help tgalati4 ... I figure it out after enabling all the views also for the second device!

Hi, 

I have the same problem and I still cannot resolve it.
Could you please detail,
in which program do you have that "Playback" tab,
where is the "recording in the capture control"?

Thanks!

---

