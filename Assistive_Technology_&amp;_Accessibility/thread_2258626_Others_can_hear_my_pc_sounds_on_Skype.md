---
title: "Others can hear my pc sounds on Skype"
date: 2014-12-29
forum: Assistive Technology &amp; Accessibility
---

### Post by tofiffe on 2014-12-29
Hi, I've recently switched to Ubuntu Gnome and installed Skype, now everyone on skype can hear my pc sounds, music, notifications, everything. How can I stop this from happening?

---

### Post by kostkon on 2014-12-29
Either your mic is picking up all those sounds, and you need to adjust the recording volume level, probably need to lower it a bit; or the recording device for Skype has been set to the monitor of your sound card and you need to install the PulseAudio Volume Control utility (aka pavucontrol) and change it back to your mic (you need first to start a call to do that.)

---

### Post by tofiffe on 2014-12-29
I don't seem to find the option to disable that in pavucontrol, I've only managed to either completely mute the microphone or make it very loud, also creating background noise...

---

### Post by kostkon on 2014-12-29
> **tofiffe said:**
> I don't seem to find the option to disable that in pavucontrol, I've only managed to either completely mute the microphone or make it very loud, also creating background noise...
No, start a call in Skype, then open pavucontrol and click on Recording.

---

