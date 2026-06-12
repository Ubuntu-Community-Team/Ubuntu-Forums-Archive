---
title: "so much troubles... black screen on zenbook after update 50-synaptics.conf"
date: 2013-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by LudoTW on 2013-10-16
A little background:
It takes a lot of patience, really, to deal with all the issues I've had with the marriage of my ux32vd and ubuntu. First in 12.04 the whole system would regularly hang, noticeably when browsing. I lived with it for some time until I installed 13.04 and then it seemed all is good.
Not long ago I decided to install CUDA, and nvidia's proprietary drivers. This made unity disapear. A whole day of trying to get this back... And I got it back...
Then yesterday for some totally unknown reasons, the tap to click function of my touchpad disapeared. The only thing I installed at the time was "processing", a nice programing language, and wrote some program with it and for arduino using the arduino ide. Whether or not it has anything to do with the touchpad issue, I know not.
But I find a way to restore the tap to touch, first test it with:

[FONT=courier new]synclient "TapButton1"=1 [/FONT]

All is well, it works.
I then proceed to make the change permanent by modifying:

[FONT=courier new]50-synaptics.conf[/FONT]

I add at the end of the first InputClass section:
[FONT=courier new]Option "TapButton2" "2"
Option "TapButton3" "3"[/FONT]

Then restart my computer.

**_The problem:_**

One new trouble! The splash screen passes normally, but then no screen to input my password, nor do I hear the drum sound: only a black screen with a cursor in the top left corner.
[FONT=courier new]fn + f1[/FONT] to sleep, then wakeup is to no avail. Reboot, hard power off (so many times) doesn't help. 
I tried to go into recovery mode but just can't: while the bios is loading, pressing "shift" doesn't do anything, the splash screen still appears followed by a black screen.
An external monitor connected on the HDMI port doesn't help either...

What happened?
What else can I try to do to either go into recovery mode or best restore my system?

Thank you...

---

### Post by LudoTW on 2013-10-17
The undeniable advantage to be in trouble is that one learns. This happened again here.
Ok this is solved. But remains unknown why I lost the tap to click function.
Here is how I solved my problems.

1) booting in recovery mode. 
Pressing the "right" shift key did it. 
I had found that the left shift was the key from [http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode](http://askubuntu.com/questions/172319/how-can-i-start-in-safe-mode) and didn't try the right one.

2) in recovery mode, failsafeX didn't work: no screen found. Reading the error messages there I found there was some problem with [FONT=courier new]50-synaptics.conf[/FONT], an unknown option 1.
What happened is that after testing in a terminal the tap to click function with 
```
synclient "TapButton1"=1
```
I copied this syntax in 50-synaptics.conf:
```
Option "TapButton1" 1
```
You notice the absence of "" around the 1? This caused troubles.
It should have been
```
Option "TapButton1" "1"
```

3) I copied the backup of 50-synaptics.conf~ to 50-synaptics.conf
But then after login, the screen resolution is frozen at 640x480

4) To solve the low resolution issue I edited [FONT=courier new]/etc/X11/xorg.conf[/FONT], 
and replaced:
    [FONT=courier new]HorizSync 28.0 - 33.0
    VertRefresh 43.0 - 72.0[/FONT]
with
    [FONT=courier new]HorizSync 30.0 - 83.0
    VertRefresh 56.0 - 75.0[/FONT]

5) I added the options of my choice for the touchpad in 50-synaptics.conf:
```
Option "TapButton1" "1"
Option "TapButton2" "3"
Option "TapButton3" "2"
```

Now I'm back with tap to click and a "normal" system. Still some work to do with the nvidia driver.

---

