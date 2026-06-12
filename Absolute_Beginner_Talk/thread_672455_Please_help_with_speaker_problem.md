---
title: "Please help with speaker problem"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Dudeman02379 on 2008-01-19
I have a Bose speaker set.  It has one subwoofer and two desktop speakers.  They only have usb output.  They work fine in windows but in ubuntu they weren't making any sound.  I went into system, preferences, sound and changed all the outputs to usb audio instead of auto detect.  After a reboot my speakers just scream this insanely loud insanely obnoxious beep.  The only way to shut them up is to unplug them.  I tried changing the settings back to auto detect but they wont stop making this noise.  I can put the volume on mute and they still BLAST this painfully bad noise.  Do I need some kind of driver for usb speakers?  Do I need to do some sort of configuration for them?  Please help I would really like to be able to use sound in ubuntu.

EDIT:  After rebooting the noise stoped but now I have zero sound.  Any halp would be greatly appreciated!  Thanks.

---

### Post by jeffus_il on 2008-01-19
You need to load a kernel module snd-usb-audio.
```
sudo modprobe snd-usb-audio
```
To check if it is loaded:
```
lsmod | grep snd-usb-audio
```

I think it should have been loaded automatically, The driver showed up in Preferences>Sound, but check it out anyway.

If the modules is loaded, check dmesg for errors, if you do a modprobe it will be at the end of dmesg, else try grep dmesg.
```
dmesg | grep snd
```
If all this fails search the forum and google for snd-usb-audio.

---

### Post by Dudeman02379 on 2008-01-20
Thanks for the reply but it didn't work.  I can choose usb audio as the device but when I hit test no sound comes out.  I tried to reboot and still nothing.  I'll keep searching but if anyone has any more suggestions please let me know!

---

### Post by jeffus_il on 2008-01-20
Try this, it for edgy, but the driver is the same:
[http://ubuntuforums.org/showthread.php?t=297835](http://ubuntuforums.org/showthread.php?t=297835)

---

### Post by Dudeman02379 on 2008-01-21
I tried that also.  Still just a loud tone noise blasts through the speakers when I click test.

---

