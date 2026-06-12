---
title: "Gamepads and joystick installation in ubuntu?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Xzallion on 2006-06-08
I would like to know how to install some gamepads and joysticks in ubuntu.
I have a MakoPad PC gamepad, and a Logitech WingMan Extreme Digital 3D Joystick, and a Saitek ST50 Joystick.  I mainly want to use these with ZSNES.

Thanks in advance.

---

### Post by nalmeth on 2006-06-08
Hey I have the same joystick as you! Can't tell you much about it though, my computer didn't come with a port for it, so I haven't been able to try. I do most of my gaming on my xbox anyway, but I'll get to it soon enough.

I don't know the logistics of installing these devices, but I remember an option in Automatix called "making most gamepads and joysticks work".

Try out automatix for a start.

---

### Post by %hMa@?b&lt;C on 2006-06-08
from my experience, Logitechs run out of the box.  

```
sudo apt-get install jscalibrator
```
and then
```
jscalibrator
```
from the terminal should show if it is working

---

### Post by Xzallion on 2006-06-08
I ran jscalibrator, but joystick initialization failed.  It gave me this message.> Could not access the specified path(s), verify that the path(s) are specified correctly and that you have sufficient permission to access them.  Also make sure that the joystick in question is actually connected, turned on (as needed), not in use by another program, and that the joystick driver or module is loaded (type 'modprobe <driver_name>').

Now I am really lost.  I should probably mention the Wingman is old, real old (a friends dad gave it to me) and may be broken, I can't even get it working in windows, through usb or through the gameport.  So I am kinda ignoring that one for now, unless someone has random advice on possible ways of fixing it.  Its the MakoPad PC and the Saitek ST50 that i need to figure out how to get working.  I may have to just break down and buy a new computer controller.

---

### Post by aeidman on 2006-06-08
[QUOTE=Xzallion]I ran jscalibrator, but joystick initialization failed.  It gave me this message.

Now I am really lost.[/QUOTE]

Same results for me.  Anyone know where to find info?

---

### Post by nalmeth on 2006-06-08
Read the error carefully

try:
sudo jscalibrator

If you still get the error, try running the automatix joysticks option, then try again.

---

### Post by Xzallion on 2006-06-08
I tried running it with sudo, that gave me the same error.  I'm going to look into automatix.  I will post what happens here in awhile.

---

### Post by Kupopo on 2006-06-08
Maybe you already took care of this, but did you make sure jscalibrator was pointing to the right path for your joystick?  Mine defaults to /dev/js0, while my joystick gets put on /dev/input/js0.

---

### Post by jobezone on 2006-06-08
[QUOTE=Xzallion]I ran jscalibrator, but joystick initialization failed.  It gave me this message.

Now I am really lost.  I should probably mention the Wingman is old, real old (a friends dad gave it to me) and may be broken, I can't even get it working in windows, through usb or through the gameport.  So I am kinda ignoring that one for now, unless someone has random advice on possible ways of fixing it.  Its the MakoPad PC and the Saitek ST50 that i need to figure out how to get working.  I may have to just break down and buy a new computer controller.[/QUOTE]

Never tried pluggin a joystick myself, but try this to see what's happening when you plug in the joystick. In a terminal run:
```
tail -f /var/log/messages
```
Then plug in the joystick to your usb port, and see what messages appear in the terminal.

---

### Post by Xzallion on 2006-06-11
I installed and ran Automatix.  There wasn't an option for joysticks/gamepads.  But its a neat program none-the-less.  So that was a dead end :(

jobezone, that code gives me an error when I use it.

```
kenneth@kenneth-ubuntu:~$ tail -f /var/log/messages
Jun 11 12:54:43 kenneth-ubuntu gconfd (kenneth-5095): Resolved address "xml:read only:/var/lib/gconf/debian.defaults" to a read-only configuration source at posi tion 3
Jun 11 12:54:43 kenneth-ubuntu gconfd (kenneth-5095): Resolved address "xml:read only:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): starting (version 2.14.0), pi d 6718 user 'root'
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): Resolved address "xml:readonl y:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at positio n 0
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): Resolved address "xml:readwri te:/root/.gconf" to a writable configuration source at position 1
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): Resolved address "xml:readonl y:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position  2
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): Resolved address "xml:readonl y:/var/lib/gconf/debian.defaults" to a read-only configuration source at positio n 3
Jun 11 12:55:06 kenneth-ubuntu gconfd (root-6718): Resolved address "xml:readonl y:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 11 12:55:36 kenneth-ubuntu gconfd (root-6718): GConf server is not in use, s hutting down.
Jun 11 12:55:36 kenneth-ubuntu gconfd (root-6718): Exiting

```

---

### Post by ramcosca on 2006-06-12
I'm having sort of the same problem. I plugged in a USB controller my girlfriend gave to me for birthday, set the buttons the first time and the emulator froze. After that, the controller is just... dead there. The emulator doesn't sense it. I did a lsusb and it does show up connected to the computer. Any suggestions that could help us?

---

### Post by Xzallion on 2006-06-15
Okay I just want to get the Interact MakoPad PC gamepad working now, so I can use it in ZSNES.  It is hooked up through a gameport/controller porth on my soundcard.  How would I got about finding and installing drivers for it?  I ahd no luck with the joysticks and really would like to get this gamepad working if its possible.

---

### Post by rcatman on 2006-09-23
ZSnes is a great emulator, thus far... I like that it has a gui. In the past,  when I was using emulators in linux i had to run a command from the command line , so its nice to have a gui to set up everything. 

I'm having a similar problem as other people and I'm positive someone knows this! 

I've installed joystick, jscalibrator, everything looks great. Joystick works :) (joystick is a logitech precision i bought for 10 bucks at frys hehe)

But zsnes can set keys to the buttons but not the diagnol :( 

The joystick is at /dev/input/js0

i've tried snes9x but it only trys to detect joysticks at /dev/js[0|1|2|etc]

EDIT: d-pad now works when running zsnes as root (sudo zsnes). dont know why, but it works.

help?

---

### Post by bolk on 2006-11-05
I have the same problem as rcatman: joystick buttons work zsnes, but the directional pad does not.

Everything works fine in jscalibrator.

Has anyone a solution for this?

---

