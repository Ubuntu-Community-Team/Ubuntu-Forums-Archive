---
title: "logitech mx400 mouse config"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by cornelious on 2007-10-27
Sorry for the extreme newbie post, long time windows user that got fed up, so here I am:)
I have tried for hours to get my mouse "back" and "forward" buttons to work.  I've tried at least 5 tutorials, and NOTHING!  I'm sure I'm doing something wrong.  Here is my xorg.conf
mouse data
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"Explorerps/2"
	Option          "ButtonMapping"         "1 2 3 6 7" 
        Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Any help anyone can gave would be great.

---

### Post by TeaSwigger on 2007-10-27
First, hello and welcome. Whether you get back or forward extra mousy buttons, I hope you'll feel that moving to ubuntu is a nice step forward in many ways.

I have a Logitech Mx310 and I haven't figured those darn buttons out. Is that similar I wonder, with two side buttons and an extra middle one under the wheel? Anyway I wouldn't mind knowing how to set 'em myself, that is besides this tool:

btnx
[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)

It does work and is marvelously configurable. Impressive tool. Problem is I haven't yet figured out how to keep it working every time I boot, I keep having to open and restart that tool. It's all I know so far but maybe that'll help you in some way :)

---

### Post by cornelious on 2007-10-27
Thank you TeaSwigger!!!  So, I followed steps, but after the first step of adding the dependencies "sudo apt-get install build-essential libgtk2.0-0 libgtk2.0-dev libglade2-0 libglade2-dev pkg-config" I tried it out, and the buttons work!  I rebooted and did nothing more and they still work.  I don't know if that will help you with having to restart the program every time, but you sure helped me and i appreciate it.

---

