---
title: "No left channel after crash."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Angry penguin on 2008-02-17
Hey guys, Im using Gutsy with compiz-fusion and just started using Miro. I was watching a video in Miro when the program crashed. When I restarted it I only had sound coming into my headphones from the right channel. How do I get my stereo sound back? 

I have rebooted a couple times and that doesnt seem to help. I booted into windows to make sure the hardware was fine and everything is cool. So somehow my sound in Ubuntu has been switched to mono. How do I fix this?

Thanks.

---

### Post by tgalati4 on 2008-02-17
Check that all the channels and switches are enabled in Volume Mixer.  Edit-->Preferences.

---

### Post by Angry penguin on 2008-02-17
everything is enabled.

---

### Post by tgalati4 on 2008-02-17
Look for a miro configuration file (perhaps .miro) and edit it or delete it.  If that doesn't work, then remove miro and reinstall.

---

### Post by Angry penguin on 2008-02-17
there are no sound configuration settings in MIro, that I could find. it probably just uses sound configuration settings from ubuntu. 

The sound problem is occurring not just in Miro, but no matter what I do in Ubuntu, everything is in mono.

There are also no configs in .miro. for sound.

---

### Post by tgalati4 on 2008-02-19
Post the output of:

aplay -l

---

