---
title: "Game controller support?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-02-26
Where can I find any kind of control box that will let me see if my game controller is working?

On that note, I have it plugged in, it has worked in the past, but zsnes doesn't want to detect it right now. 

Where can I look to see if this is an Ubuntu problem or a zsnes problem?

---

### Post by linuxfanatic1024 on 2007-02-26
If you're using KDE, you can go to System Settings, then click on Keyboard and Mouse, and there's a Joystick configuration there.

If you're using GNOME, you may have to instead install the package called **joystick** using Synaptic or Adept, and then open a terminal and type
```
jstest
```

and hit Enter.

---

### Post by ramjet_1953 on 2007-02-26
There is a package available through Synaptic called [COLOR="Red"]jscalibrator[/COLOR] , that allows you to test and calibrate a joystick. I assume it would probably work with other types of controllers, as well.

Regards,
Roger :cool:

---

### Post by linuxfanatic1024 on 2007-02-26
I never got that program to work. :(

---

### Post by jonsayer on 2007-02-26
Ok, i got that. Now how on earth do i use it?

---

### Post by jonsayer on 2007-02-26
i mean the "joystick" program for gnome. 

Usage: jscal <device>

  -c             --calibrate         Calibrate the joystick
  -h             --help              Display this help
  -s <x,y,z...>  --set-correction    Sets correction to specified values
  -t             --test-center       Tests if joystick is corectly calibrated
                                       returns 0 on success, see the jscal
                                       manpage for error values
  -V             --version           Prints the version numbers
  -p             --print-correction  Prints the current settings as a jscal
                                       command line

What should I be typing next? I have tried the letters to the left, all send back a syntax error

---

