---
title: "[SOLVED] Having problems with sound"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-03-29
I am new to Ubuntu, I am having problems with my sound.  The sound works and everything but when I am using Rhythmbox or any other program the master volume does not control the volume in that program.  I also have buttons on my computer that let me control the volume from my PC, these buttons are built right into the computer.  These buttons don't control the master volume or anything.  For some reason when I try and use these buttons at big speaker comes onto the screen and it looks as if I am controlling the volume but it doesnt control the volume.

Computer Specs:

description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by FuturePilot on 2008-03-29
Go System&#8594;Preferences&#8594;Sound and make sure that at the bottom you have Master selected as the one to control with the keyboard.

---

### Post by herbster on 2008-03-29
Most likely you simply have the wrong mixer selected. Right click the volume icon and I believe it's preferences or select mixer, I can't recall, but you can select which mixer to use. You want to use PCM Master or PCM. Have a song/video playing and raise/lower the levels of different ones to see which one changes the volume.

---

