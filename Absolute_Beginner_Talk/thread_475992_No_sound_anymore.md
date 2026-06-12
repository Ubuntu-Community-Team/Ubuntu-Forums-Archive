---
title: "No sound anymore"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Jamester64 on 2007-06-16
After trying to get tv card and webcam working using camstream and tvtime I no longer have sound
I have uninstalled those apps and still no sound on Audigy 2 zs

Please help

---

### Post by weel on 2007-06-17
Can you tell us what operating system and version you are running, and what window manager / desktop system?

Can you run the following commands and post the output?

ps ax | grep arts
ps ax | grep esd
lsof | grep alsa
lsmod | grep snd

Have you rebooted the machine?

And, at the risk of sounding condescending, I'm going to have to ask: have you made sure there is an audio output device connected to the right bus and that it is on and not broken?

---

