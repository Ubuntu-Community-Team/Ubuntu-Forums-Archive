---
title: "[SOLVED] Any Apps That Integrate with Context Menu?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-10-27
Hi everyone,

One of the things I really liked about Windows was the fact that there were lots of applications that would integrate with the context menu (i.e., the "right-click menu"). Are there any of these available for Ubuntu?

Specifically, it would be great if there were audio conversion functions available via the context menu (similar to the Windows program DBPowerAmp) and encryption available too.

So far, I've heard about something called Nautilus-Actions but it requires creating scripts, etc., which is to advanced for me at this stage. 

Thanks,

Plinydogg

---

### Post by Campingman on 2007-10-27
There is Nautilus-Open-Terminal which is in Synaptic Package Manager, a useful application that will open a terminal in whatever window you are in.  It saves trying to navigate to the correct folder with terminal commands.

---

### Post by plinydogg on 2007-10-27
Cool. Thanks!

---

### Post by plinydogg on 2007-10-27
I found several nifty context menu plugins but one of the most useful doesn't appear to work in Gutsy (I tried rebooting, etc.). It is nautilus-script-audio-convert. Anyone know how to get this working?

---

### Post by plinydogg on 2007-10-27
I found the solution: after installing nautilus-script-audio-convert, you have to type this into the terminal:

nautilus-script-manager enable ConvertAudioFile

The reason for this (and the solution) can be found here:

[https://bugs.launchpad.net/ubuntu/+source/audio-convert/+bug/130055]("https://bugs.launchpad.net/ubuntu/+source/audio-convert/+bug/130055")

---

