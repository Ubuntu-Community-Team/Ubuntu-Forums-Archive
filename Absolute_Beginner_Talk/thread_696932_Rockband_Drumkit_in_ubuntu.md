---
title: "Rockband Drumkit in ubuntu"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by cl_audio on 2008-02-14
Just curious if it's possible to use the rockband drums in ubuntu, basically, the windows hack, using joytokey you are able to bind each pad to a letter, then in a synth program (in ubuntu's case, I would recommend hydrogen) you would be able to hear your output as each key is bound in the program to a drum. 


Is this possible?


Thanks in advanced!

---

### Post by Crooksey on 2008-02-14
When you plug in in run 
```

dmesg
```

And post results.

---

### Post by oisuxx on 2008-02-18
i was wondering the same thing. if i did this also is there any specific thing we should be looking for in the dmesg box?

---

### Post by HEDGECORE on 2008-02-22
```
[418464.325962] usb 3-2: new full speed USB device using uhci_hcd and address 2
[418464.536705] usb 3-2: configuration #1 chosen from 1 choice
[418464.789474] usbcore: registered new interface driver xpad
[418464.789483] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6

```

I assume that's what you're looking for.  Now, what to use it with?  Does Hydrogen support USB devices or just MIDI?

*Edit:  Instructions to install the kernel module are here:  [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

