---
title: "disable beep on boot up"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by dugh on 2007-06-27
I turned off the system beep in the gnome control panel, the gnome terminal preferences, and in the /etc/bash.bashrc file, but now I am getting a beep right when booting up (near the end of the boot process).  I seem to recall that is supposed to mean something, but I don't know what. 

How can you disable the beep totally, or do I just need to turn off the motherboard speaker in the bios?

---

### Post by logos34 on 2007-06-27
If it's just a short beep then most likely it's the bios's way of saying everything a-ok.  If it's a long beep, then it might be an error signal--check your motherboard documentation for bios beep patterns and what they mean (each bios is different).  If you want to disable it you'll have disable it in the bios or physically remove it (some just plug into pin headers on the board.). Personally I wouldn't disable it unless it really loud and obnoxious--because it indicates what the problem is if there is one.

---

### Post by dugh on 2007-09-01
No it's not a beep from the bios, it is something when gnome is loading up that beeps.
I would like to turn off all beeps.  The system preferences turns off the speakers but not the motherboard speaker.

---

### Post by dugh on 2007-09-01
"pcspkr" is the magic keyword I was looking for.  Here's how to disable the motherboard speaker:
[http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep](http://www.thinkwiki.org/wiki/How_to_disable_the_pc_speaker_(beep)!)

---

### Post by dugh on 2007-10-14
The instructions I linked to for removing them are no longer there, so here are the instructions:

Open the terminal applications (under applications->accessories), and type these commands:

sudo rmmod pcspkr

sudo gedit /etc/modprobe.d/blacklist

And paste this line at the bottom of the file then save it:

blacklist pcspkr

If you ever want to re-enable the speaker type: sudo modprobe pcspkr

---

