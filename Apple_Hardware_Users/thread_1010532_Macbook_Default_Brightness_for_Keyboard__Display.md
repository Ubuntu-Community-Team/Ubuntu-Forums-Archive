---
title: "Macbook Default Brightness for Keyboard / Display"
date: 2008-12-13
forum: Apple Hardware Users
---

### Post by undoIT on 2008-12-13
I've got the Macbook 5,1 and when I boot into Ubuntu, the brightness resets to maximum for both the backlit keyboard and monitor. Is there any way to adjust this, so that the monitor is at the lowest brightness setting while booting and after X loads and also so the keyboard backlight is turned off by default?

---

### Post by Sameer Sundresh on 2008-12-14
I have a MacBook Pro 4,1.

While I don't know how to adjust the backlight brightness pre-boot, after loading the mbp_nvidia_bl module, I was able to set the backlight brightness via gnome-power-preferences; this setting is reinstated by gnome-power-manager when you log in.  You need to run "sudo modprobe mbp_nvidia_bl" for this to work; to make the module load at every bootup, add mbp_nvidia_bl to /etc/modules.  Alternatively, you can "echo 1 > /sys/devices/virtual/backlight/mbp_backlight/brightness" in your /etc/rc.local to make this happen earlier in the boot process (brightness values range from 0 to 15 on my system).

The keyboard light defaults to off for me, but I've found that you can echo a brightness value (appears to be in the range 0-255) to "/sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness".  You need to load the applesmc module for this to work: "sudo modprobe applesmc".  So you could, for instance, add applesmc to /etc/modules, and edit /etc/rc.local to adjust the keyboard backlight on bootup.

A few other things you may find useful:

1. applesmc allows you to adjust the minimum and maximum speeds for the two fans, or if you desire, you can even manually set the fans to a particular speed (be careful).  Just look around in /sys/devices/platform/applesmc.768 (it may be a different number for your computer).

2. applesmc also allows you to read the values of several temperature sensors.

3. nvidia-settings allows you to adjust the GPU and video memory clock speeds (e.g., make them slower to save power).  To enable clock speed adjustment view the nvidia-settings GUI, you need to add the line
Option "Coolbits" "1"
to the Device section(s) of your /etc/X11/xorg.conf file.  The nvidia-settings program can also be used as an entirely command-line driven program, so you can script it to automatically load predetermined settings (check the man page).  You'll need to apt-get install nvidia-settings to get it.

4. At least for my computer, the keyboard repeat rate was much faster than what the settings in gnome-keyboard-properties would seem to indicate.  This resulted in backspace going too fast, etc.  I'm not sure if this is because I'd increased the (by default, overly slow) keyboard repeat rate in Mac OS X.  But my solution was to run "kbdrate -d 250 -r 1" in /etc/rc.local (you can also sudo and run this... but for some reason it works from a console login (Ctrl-Alt-F1) but not from within X...).  The 1 there means 1 character per second, but it's actually much faster than that--probably in the range of 5-10 cps.

5. The gsynaptics (GUI) and syn-client (command line) programs allow you to fine-tune the settings of your touchpad; you can then add these settings to an InputDevice section of your /etc/X11/xorg.conf file.  This lets you do things like adjust tracking speed, adjust how clicks are detected, program multi-finger clicks for the middle and right buttons, and enable horizontal two-finger scrolling (only vertical was on by default for me).  I only found out about this because tap-to-click wasn't working at all by default for me; since as I understand the 5,1 doesn't have a discrete trackpad button, this may be even more important for you.

---

### Post by olavjunior on 2008-12-29
> **Sameer Sundresh said:**
> I have a MacBook Pro 4,1.
The keyboard light defaults to off for me, but I've found that you can echo a brightness value (appears to be in the range 0-255) to "/sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness".  You need to load the applesmc module for this to work: "sudo modprobe applesmc".  So you could, for insance, add applesmc to /etc/modules, and edit /etc/rc.local to adjust the keyboard backlight on bootup.


Im not quite in to this echo thing. Tried ```
sudo echo 150 | /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
```
both in X and in tty1, but got permission denied each time. Could you point me out in the right direction here?

And by the way, have you any idea on how to tap and drag? I'm having difficulties with that one.. EDIT: Oh, click and drag with the same finger. I must say Im more fund of the way osx do it cause theres no click at the top, so click and drag upwards is kinda hard...

---

### Post by mkvnmtr on 2008-12-29
I dodn't know about your macbooks but on my 8.04 install I have an icon on the top panel that controls brightness. I don't remember if it came with the install or the Gdesklets package that I installed. I just right clicked on the panel and choose add to panel and found it in the list. Works rather well.

---

### Post by _mario_ on 2008-12-30
> **olavjunior said:**
> Im not quite in to this echo thing. Tried ```
sudo echo 150 | /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
```
both in X and in tty1, but got permission denied each time. Could you point me out in the right direction here?


yes, it's:

```
echo 150 | sudo tee /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
```

ciao,
Mario

---

### Post by olavjunior on 2009-01-03
Thanks!! :D

Any ways to do this in X so that the brightness can be controlled via F5/F6?

---

### Post by Chrisj303 on 2009-01-17
It would be great if we could get a proper tutorial on this subject. Information on it seems to be really loosely scattered throughout these boards.

I've been trying for a couple hours now to get my keyboard backlight working.

" echo 150 | sudo tee /sys/devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
150"

Gives me a response, but the F5/6 keys do nothing - and the light isn't coming on at boot for me. I have the hal Applesmc .deb installed.

I can't find an /etc/modules though, which is frustrating.

---

### Post by olavjunior on 2009-01-19
To make them light up at boot time you need to do as mentioned in the first post. You need to add applesmc to /etc/modules, and add the echo command to /etc/rc.local. This did it for me. 

But you wont be able to control it via F5/F6  no matter what, cause then you somehow need to map the F-keys to the echo-command (give a relative delta value), and I don't know how to do that..

(Can't give you any more info as I'm on OSX right now)

---

### Post by Chrisj303 on 2009-01-19
Got it sorted, I was looking for a modules folder rather than a simple config file.

F5/6 work perfectly for controlling the keyboard backlight.

---

### Post by olavjunior on 2009-01-21
Haha, omg! Who figures, mine do as well :) I guess I just took it for granted they wouldn|t work :D 

The only thing that|s stopping me from an all ubuntu experience now is the display-port (digitally output)

(I|m actually impressed with how good Ubuntu does all this! It seems like a worse situation on other distros. One bugger is the keyboard though, that just won|t get mapped right  - as you all can see :) )

---

### Post by daleha on 2009-02-25
confirm that the instructions provided by mario work

---

