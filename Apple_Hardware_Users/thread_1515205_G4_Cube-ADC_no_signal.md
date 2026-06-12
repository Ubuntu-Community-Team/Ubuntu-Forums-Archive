---
title: "G4 Cube-ADC no signal"
date: 2010-06-22
forum: Apple Hardware Users
---

### Post by sliderda2b on 2010-06-22
I have installed Lucid on my G4 Cube and it works fine except that I only get a video signal on the VGA connector. I would like to use my 15" Apple Studio LCD, but cannot get a signal on the ADC connector. If I boot the the original OS 9 CD, it works, so I don't think it is a hardware problem. I have tried creating an xorg.conf file with many different setting - still no signal to the LCD. Can anyone help?

---

### Post by linuxopjemac on 2010-06-22
Connect the monitor to the ADC and see if you can issue cvt commands.

Just type without signal (so type blindly) and give me the output of:

```
cvt 1024 768
```

---

### Post by sliderda2b on 2010-06-23
After running the command, cvt 1024 768, there was no change. Still no signal at the ADC connector. Also, the VGA still works.

---

### Post by linuxopjemac on 2010-06-23
what was the output of that command with the monitor connected to the ADC ?

---

### Post by sliderda2b on 2010-06-24
The screen is blank (black) even though the power light is on and the keyboard and sound are connected the the integrated USB ports (keyboard/mouse and sound all perform as they should).

---

### Post by sliderda2b on 2010-07-01
I am still not able to turn on the ADC port on my G4 Cube. Does anyone know if the driver for the Rage 128 video card supports the ADC port? If so, what are the commands to enable it?

---

