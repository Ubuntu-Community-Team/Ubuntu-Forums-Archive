---
title: "weard screaming/buzzing sound while feisty plays sounds"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by DataMatrix on 2007-09-28
Hello all! I just moved to Ubuntu 7.04 Feisty from WinXP. I have some pririor expirience with fedora core 4, but not very much. This is my first post here
I have the following problem: My Ubuntu plays sounds, but while playing, i hear a buzzing/screaming sound (i don't know even how to call it). Here it gets worse: when i change a volume setting on the volume control panel, my computer mutes until i reboot it.
[QUOTE="aplay -l"]card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/QUOTE]
:confused::(](*,):-?:-s
I'm running a PC with MB{ Asus M2N-MX with onboard audio, AMD Athlon64 2800+ }

Can anyone please help me out, because thes buzz is freaking me out and also i want to play music on the computer. :guitar:

---

### Post by kyphi on 2007-09-28
Have a look for a volume control on the application you are using to play music.

If you are using Timidity to play a midi file, for example, the volume control has to be turned quite low. 

The volume control on the top panel is a master control - if you right click that it will give you access to the volume control panel where you can make adjustments.

---

### Post by mandrill on 2007-09-28
turn off the output jack in volume control under switches tab

---

### Post by CaptainInsaneO on 2007-09-28
Are you using onboard sound or do you have a soundcard? Right now your system is configured for onboard sound (which is crap).

---

### Post by DataMatrix on 2007-09-29
I didn't found an output jack setting in the volume control (i know were it is).
The main thing that concerns me is that all sound (including the buzz) instantly mutes whenever i change a setting.
My audio card is embedded in to the chipset (MB box says "HD Audio"). I worked perfecly on windows xp sp2, usind sound max mixer (came when i installed the MB driver)

Note: MB==Mother Board

Any more ideas?

EDIT:
The problem went away (or atleast the buzz did). I don't know how. I've done 2 or 3 updates and
```
sudo apt-get install kde
```
Note that I'm _not_ using KUbuntu.

---

