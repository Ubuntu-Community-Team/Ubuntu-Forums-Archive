---
title: "moving audio profile to output format in Sound Juicer"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by kolhoznik on 2007-06-29
I have followed the above directions in the help section of Juicer , but under Sound Juicer Preferences-Output it does not give my new mp3 profile as an audio out put option.   When I click "edit" the audio profile is there I just can't get it as an output.  I have made sure that I have clicked the "active" box so I can't think of what the problem could be?

---

### Post by reacocard on 2007-06-29
> **kolhoznik said:**
> I have followed the above directions in the help section of Juicer , but under Sound Juicer Preferences-Output it does not give my new mp3 profile as an audio out put option.   When I click "edit" the audio profile is there I just can't get it as an output.  I have made sure that I have clicked the "active" box so I can't think of what the problem could be?

You have to install the right codecs, running this in a terminal should do it (enter your password when prompted):
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

### Post by bsawler on 2007-07-01
Thanks, 
worked like a charm.

---

### Post by kolhoznik on 2007-07-05
I am a real newbie with Ubuntu, so when the above post says to install the codec in a terminal, how do I find that?

---

### Post by reacocard on 2007-07-05
> **kolhoznik said:**
> I am a real newbie with Ubuntu, so when the above post says to install the codec in a terminal, how do I find that?

Applications -> Accessories -> Terminal

---

### Post by kolhoznik on 2007-07-05
Thanks, for the help.  Its working great now.

---

