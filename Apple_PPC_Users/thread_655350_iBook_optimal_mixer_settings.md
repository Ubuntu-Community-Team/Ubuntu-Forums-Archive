---
title: "iBook optimal mixer settings"
date: 2008-01-01
forum: Apple PPC Users
---

### Post by fuoco on 2008-01-01
I was trying to play around with the mixer settings on my iBook G4 to get the best results. I mean be able to have as much control over volume without having distortion. I tried mostly changing the Master and PCM volume settings as I'm not sure what the rest do and if they are relevant. I was unable so far to get good results when compared to the results I get with the builtin speakers in OS X on the same machine.
Has anyone had better luck and can share a good configuration for the mixer that has no distortion in all volume settings?

Thanks a lot in advance!

---

### Post by curly_nostrill on 2008-01-04
I have an iBook dual usb 600 running xubuntu 'feisty'.  I find that keeping the PCM to around 50 - 60 ish with $alsamixer avoids the distortion pretty well.

I don't run gdm nor X by default.  I turned them off but didn't remove them.  The machine stays cool and snappy and runs mpd and ncmpc with music on a wireless NFS share beautifully.  The only problem is coming back from sleep mode I need to pause then resume playback to avoid the skipping syndrome.

---

### Post by JPorter on 2008-01-04
The distortion issue is usually due to the master gain being above 0.00.

Using alsamixer, check the actual gain values rather than the position of the sliders or their numeric value.  Set the master volume and pcm volumes to 0.00 gain.

You'll want to unbind the default volume buttons on the keyboard from the Ubuntu volume control, and leave the "software" volume at 0.00 gain (100%) in alsamixer, then turn down the volume in hardware using the built-in buttons once they are unbound from the software controls and cease to affect the alsamixer values.

Use "sudo alsactl store 0" to make the alsamixer setting persist across a reboot.

Hope this helps, let me know if I can rephrase all of that better.

---

### Post by fuoco on 2008-01-04
> **JPorter said:**
> The distortion issue is usually due to the master gain being above 0.00.

Using alsamixer, check the actual gain values rather than the position of the sliders or their numeric value.  Set the master volume and pcm volumes to 0.00 gain.

You'll want to unbind the default volume buttons on the keyboard from the Ubuntu volume control, and leave the "software" volume at 0.00 gain (100%) in alsamixer, then turn down the volume in hardware using the built-in buttons once they are unbound from the software controls and cease to affect the alsamixer values.

Use "sudo alsactl store 0" to make the alsamixer setting persist across a reboot.

Hope this helps, let me know if I can rephrase all of that better.

Thanks a lot. That seems all very knowledgeable but i seem to not understand exactly what I'm supposed to do. what exactly is the difference between gain and volume. i see the slider and it goes between 0 and 100. I have Master and PCM that affect the speakers. Not sure either what is the unbinding of the keys? the keys seem to affect the Mater volume, but I can change it to affect the PCM instead...

Thanks a lot in advance!

---

### Post by JPorter on 2008-01-20
> **fuoco said:**
> Thanks a lot. That seems all very knowledgeable but i seem to not understand exactly what I'm supposed to do. what exactly is the difference between gain and volume. i see the slider and it goes between 0 and 100. I have Master and PCM that affect the speakers. Not sure either what is the unbinding of the keys? the keys seem to affect the Mater volume, but I can change it to affect the PCM instead...

Thanks a lot in advance!

In alsamixer there are slider values, but these are MEANINGLESS with regard to the actual gain settings of the card.

You will want to watch the gain values as listed in the display, they are a numeric value like -30.0 or 0.0 or 3.0.   Set the MASTER and PCM values to 0.00.   This may be at 80% on the slider, or another value... the ONLY thing that matters is the GAIN value.

With this set, go into your keyboard properties in the System menu and find the section for the volume buttons.  Unbind these completely and they should continue to function, but only at the hardware level. 

All of this together results in your software "volume" being set to full, or 0.00 gain, and your hardware (amplified) volume being variable in hardware.   You won't get the on-screen volume indicators when you press the buttons, but your audio quality will be much higher.


Note:  this works well on some hardware and not well on others.  I have found this to work well for me, it may not work well for you.  Best of luck.

---

