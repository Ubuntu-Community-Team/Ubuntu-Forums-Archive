---
title: "Ready to give up on Ubuntu... (Sound!)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by sleepwalker on 2007-10-22
I have a problem with sound that I just can't seem to fix!

I do not get any sound at all during installation on my laptop. (A HP dv2125nr).

I get sound one time during a random boot within the first 10 logins (shutting down the computer and restarting.)

Is there anything that I can check? I have seen "alsa" mixer pop up alot in similar posts, yet I dunno what to configure.

From Volume Control I have:
File>Change Device>

0: HDA NVidia (Alsa mixer)
1: Conexant CX20549 (Venice) (OSS Mixer)

I had tried to install Ubuntu Studio as well, but I was receiving more errors with the install. (I couldn't even load the 'About Me' without receiving an error.)

Currently running the 64-bit version of Ubuntu 7.10

Thanks anyone...

---

### Post by steve.horsley on 2007-10-22
Two things you can try:

Firstly, use the PC BIOS to disable your on-board sound controller.

Second, double-click the speaker icon and then select Edit->Preferences. Enable every possible control and slide them up. It is possible that one of the not-shown sliders is the one you need.

P.S. Using alsamixer is actually quicker than the GUI for this - open a command prompt, expand it to full screen and enter the command **alsamixer**.

---

### Post by XFocus on 2007-10-22
I had this exact same issue when I first installed Ubuntu and was able to resolve it by doing some poking around and maxing out every volume on the mixer.  The culperate for me was the PCM volume.

---

