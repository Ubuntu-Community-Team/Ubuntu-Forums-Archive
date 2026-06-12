---
title: "Game Controller prob. jstest: command not found"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Beamvr6 on 2006-10-19
I've connected a game controller (USB Wheel and pedals) and it more or less works in a game on all axes and buttons but needs calibration. Searched a lot on all forums and using jstest and jscal seems to be on the path to do so. When I enter jstest or jscal in the terminal it returns "command not found". What am I doing wrong / need to do?

TIA

---

### Post by Beamvr6 on 2006-10-19
Some updates what I've tried after the first post:
- sudo apt-get install joystick. Result: "Package joystick is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. However the following packages replace it:
  inputattach
E: Package joystick has no installation candidate"

So I installed inputattach but reading some docs I learned it is for serial devices only. So pretty useless.

- Run jscalibrator (a GUI tool). This correctly reports all axes and buttons and also allows calibration. Save the calibration data.

- Hoping on something I started the game again and the wheel wasn't working in the game at all anymore :( :-? 

I'm using Cedega to run the game and there joystick info van be entered as it comes from jstest.


So this n00bs question remains: what I a doing wrong with this jstest thing???

---

### Post by Beamvr6 on 2006-10-19
Problem solved. I am on AMD64 and app. there isn't an "official" joystick package for that. An unoffical one however can be found here:

[http://packages.debian.org/stable/utils/joystick](http://packages.debian.org/stable/utils/joystick)

n00b is learning every day.

---

