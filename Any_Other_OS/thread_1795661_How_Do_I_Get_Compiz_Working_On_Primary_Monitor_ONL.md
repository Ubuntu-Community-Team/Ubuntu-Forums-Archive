---
title: "How Do I Get Compiz Working On Primary Monitor ONLY?"
date: 2011-07-03
forum: Any Other OS
---

### Post by Spike-X on 2011-07-03
Apologies if this has already been addressed, I've been searching the forums and Google for an answer and haven't found one.

I'm running two monitors off an Nvidia graphics card. I want Compiz to run on my primary monitor (24" Viewsonic running off DVI output), but not on my secondary monitor (32" Sony TV running off HDMI output). I only have the TV set up as a secondary monitor so I can play my video files on the larger screen.

I want to be able to run Compiz on my primary monitor with the traditional 4-desktop cube, and have the secondary monitor as a single screen to which I can drag my VLC window when required.

At the moment when I spin the cube, it spins on both monitors, which is not what I want to happen, especially if the kids are trying to watch cartoons while Daddy does Internet stuff.

A: Is what I want to do even possible, and B: if so, how?

I'm running Linux Mint 9, based on Ubuntu 10.4.

---

### Post by jocko on 2011-07-03
I don't think you can run compiz on only one screen and still be able to drag a window from one screen to another.
What you can do is run a separate x session on the tv, and start vlc on that.
Since you have an nvidia graphics card, I assume you use the proprietary driver, so you should be able to set it up easily using nvidia-settings.
Just make a backup of your xorg.conf in case you don't like how it turns out:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```Then open up nvidia-settings with root permissions:
```
gksudo nvidia-settings
```In the "X Server Display Configuration" tab, select your tv, press "Configure" and pick the second option ("Separate X Screen"). Then press "Save to X Configuration File".
Next time you log in you will have two screens, one on the monitor and one on the TV. You'll be able to move the mouse pointer between the screens, but you will not be able to move windows between screens.

Note that the screen on your tv will probably start without a window manager. To fix that, start unity by:
```
DISPLAY=:0.1 unity --replace
```.
I haven't figured out how to get a unity launcher on the second screen, so for now you'll have to start your programs from the first screen by adding "DISPLAY=:0.1" before the command.
So to start vlc:
```
DISPLAY=:0.1 vlc
```Or make a custom launcher on your desktop.


And, to get everything back to the way it was before:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

EDIT: Didn't notice you run mint. The unity part will obviously not work for you...

---

### Post by Perfect Storm on 2011-07-03
Moved to Other OS/Distro Talk.

---

### Post by jocko on 2011-07-03
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.
Why?
Even if the OP uses linux mint, the question itself, and the solution to his problem is valid for ubuntu aswell.

---

### Post by Lucradia on 2011-07-03
> **jocko said:**
> Why?
Even if the OP uses linux mint, the question itself, and the solution to his problem is valid for ubuntu aswell.

Plus One.

---

### Post by Spike-X on 2011-07-03
> **jocko said:**
> 
EDIT: Didn't notice you run mint. The unity part will obviously not work for you...

Yeah. I tried using ```
DISPLAY=:0.1 metacity --replace
```

but that caused Compiz to stop working on my primary monitor.

---

### Post by Perfect Storm on 2011-07-03
> **jocko said:**
> Why?
Even if the OP uses linux mint, the question itself, and the solution to his problem is valid for ubuntu aswell.

Mint is not ubuntu, even if the solution is the same in this case. Mint have their own forums - please read the stickies of 'Other OS/Distro Talk.

---

### Post by jocko on 2011-07-03
> **Spike-X said:**
> Yeah. I tried using ```
DISPLAY=:0.1 metacity --replace
```but that caused Compiz to stop working on my primary monitor.
I've just tried this in a normal gnome session, and I get it working fine by running compiz on both screens:
```
DISPLAY=:0.1 compiz --replace
```

---

