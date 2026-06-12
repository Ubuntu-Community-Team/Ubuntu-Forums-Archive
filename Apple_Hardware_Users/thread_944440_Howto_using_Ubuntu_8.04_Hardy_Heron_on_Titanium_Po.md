---
title: "Howto: using Ubuntu 8.04 Hardy Heron on Titanium Powerbook"
date: 2008-10-11
forum: Apple Hardware Users
---

### Post by msikma on 2008-10-11
I figured I'd share my experience with a 500 MHz Titanium PowerBook.  Installing [Hardy](http://cdimage.ubuntu.com/ports/releases/hardy/release/) is possible, but you'll need about 384 MB RAM at the very least.

The problem, in my case, was the video card.  I have an **ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)**.  When booting the Live CD (not the alternative CD, that is), the screen turns glitchy white and the system won't boot.

First, boot the system by typing **live-nosplash vga=1** at the prompt.

The system will start booting and eventually end with a glitchy screen as X is being started.  What we should do is go to a tty by pressing CTRL+ALT+F1 (or any other function key other than F7).  We should reconfigure x.org, as it was not able to correctly determine our screen's settings.

Type **sudo nano /etc/X11/xorg.conf** to edit the configuration file.  Since this is a Live CD, you don't need to worry about making a backup, though this is normally a good thing to do.

Now head over to the section "Device" and add:
[INDENT]Driver "ati"[/INDENT]
Then, in section "Monitor", add:
[INDENT]HorizSync	30-60
VertRefresh	50-75
Option		"DPMS"
Modeline	"1152x768" 65 1152 1178 1314 1472 768 771 777 806 +HSync +VSync
[/INDENT]
(Those values were taken from [saweso.com](http://www.saweso.com/uber-linux/apple-titanium-powerbook/)--thanks!)
In the section "Screen", we should add the following:
[INDENT]DefaultDepth	24
SubSection "Display"
	Depth		24
	Modes		"1152x768"
EndSubSection[/INDENT]

Now close the file by pressing CTRL+X and then choosing Y to save our modifications.

We're ready to start X now, but for some reason nothing happens when you try to do it as the "ubuntu" user, so instead we'll type **sudo startx**.  It might tell you that the X server is already active; if that's the case, follow its instruction to remove /tmp/.X0-lock before trying again (**sudo rm /tmp/.X0-lock** will do the trick).

Finally, in order to install Ubuntu, just head over to /home/ubuntu/Desktop/ and click on the installer icon.

---

### Post by sirthorn on 2009-05-07
Just thought I'd add that this also works to get Jaunty installed on the same hardware.

It's very sluggish on this old beast of a laptop, but it does work if you are willing to put up with it.

---

