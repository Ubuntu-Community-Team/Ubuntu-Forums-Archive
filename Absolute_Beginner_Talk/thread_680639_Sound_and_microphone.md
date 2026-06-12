---
title: "Sound and microphone"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by hrafninn on 2008-01-28
I have a Dell Precision M4300.  The sound is working fine (after I followed Method A in [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)).  However, the internal microphone is not working and I can't get it to work. Can anyone help?

Here is what I see in Volume Control and Sound Recorder:

In Volume Control (Edit-Preferences) the following are checked:

Master, PCM, Front, Capture, Capture1, Digital, Digital Input Source, Input Source (actually twice). In the "Recording tab" I can only see Capture, Capture 1 and Digital. In the "Options" tab, Input Sorce is "Front mic".

When I run Sound Recorder, the drop down box "Record from input" shows: Digital, Capture, Cpature1, Mux, Mux1.  There is no mic entry there.

---

### Post by Nepherte on 2008-01-28
What version of Alsa are you using? I've had the same problem with my sony laptop (cfr. signature) and upgrading to 1.0.15 solved my problem. It gave me an extra checkbox where I could enable the internal micro.

---

### Post by hrafninn on 2008-01-28
How can I see the Alsa version (what does Alsa stand for anyway)?

I have tried a number of things, and it seems that the microphone is currently working!  At least I can be heard in Skype and I can record a sound in "Sound recorder" using Capture (by the way, what is the difference between Capture, Capture1, Digitial, Mux and Mux1?).

I'm not sure what made it work.  Maybe: 

sudo asoundconf set-default-card Intel

However, the drop down box "Record from input" in Sound recorder still does not show a mic entry.  Shouldn't there be one?

---

### Post by Nepherte on 2008-01-28
To see the version you are using:
```
cat /proc/asound/version
```

If it it works now, I wouldn't be worried anymore. Dunno if the micro entry should be there, I guess it should be there :s

p.s. ALSA stands for Advanced Linux Sound Architecture.

edit: you might want to check this page starting from 'Manually specify module parameters' : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by cdtech on 2008-01-30
Use
```
alsamixer
```

Press f5 to bring up all controls and select IntMic using the arrow keys. Press the space key to select as the capture. You should be able to use the mic now. You might have to select the LineIn, but the IntMic works for me.

Hope this helps......

---

