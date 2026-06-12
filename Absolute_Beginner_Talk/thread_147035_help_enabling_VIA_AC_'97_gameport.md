---
title: "help enabling VIA AC '97 gameport"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by markiss on 2006-03-19
I have been racking my brains and reading hundreds of web pages trying to get get help with my gravis gamepad. I think its a problem with the port. I've tried everything from accessing froom root to installing drivers. Can anyone help?

---

### Post by navilon on 2006-03-19
did this port work with your pprevious operating system?

---

### Post by markiss on 2006-03-19
I am running Windows XP on a seperate HD, my old gravis gamepad works fine over there. I'm new to both Linux and Ubuntu, so I'm not entirely sure that I've done everything right. 

Niether jscalibrator, nor jscal recognizes the gamepad. The files are there I think, at **/dev/js0**, and **/dev/input/js0**

in another post I found this:

[B]sudo modprobe joydev
sudo modprobe emu10k1-gp
sudo modprobe analog
sudo modprobe grip[/B]

and

[B]sudo rm -f /dev/input/js0
sudo rm -f /dev/js0
sudo mknod /dev/input/js0 c 13 0
sudo ln -s /dev/input/js0 /dev/js0[/B]

i've executed all these commands as root as well. I dont get any errors. I am thinking its a problem with the port not being configured right?

what next? I really want to use this gamepad to play my Mame games and my Snes, and Genesis game. Thanks in advance for any help.

Markiss

---

