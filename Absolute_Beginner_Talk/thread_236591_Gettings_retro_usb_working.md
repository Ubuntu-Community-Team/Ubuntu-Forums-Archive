---
title: "Gettings retro usb working"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-08-15
I bought a USB NES controller kit to convert a nes controller to usb.  It is recognized by device manager but I cant get it to work in gfceu, a nes emulator.  It seems js0 is being recognized as my keyboard for some reason by  joystick calibration.  So I did jscal -c /dev/input/js1

It lets me calibrate it but I dont understand it.
Move axis 0 to minimum position and push any button.
I move the dpad but it doesnt seem to work.... i dont know what to do.

Do I hold the dpad and hit a key or the A button.... not sure.

---

### Post by GuitarHero on 2006-08-15
Its listed as /dev/input/event3

---

### Post by GuitarHero on 2006-08-15
bump

---

### Post by GuitarHero on 2006-08-16
The config in gfceu think s a button is being pushed because it automatically goes through A1 and A2 and goes to B1.  I dont know whats actually happening.

---

### Post by GuitarHero on 2006-08-18
bump

---

