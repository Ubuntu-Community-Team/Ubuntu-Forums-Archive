---
title: "Black Screen after Edgy install on Inspiron 1100"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-11-12
Hello all,
I just upgraded to Edgy on my Inspiron 1100. Now the screen is black and there seems to be very little I can do. I can hit CTRL+ALT+F1 to get a terminal, but I don't know what to do to get this thing working again. Does anyone have any ideas?

Also, when the machine boots, it eventually comes up to a screen saying that X Windows couldn't start. Could this be a configuration issue?

Will

---

### Post by joshsherman on 2006-11-13
When the screen comes up telling you of the problem loading X, there should be an explanation of the issue, along with the option to display more details.

That should point you in a better direction to solving your issue.

-j

---

### Post by gantww on 2006-11-13
There is a message that comes up, but it doesn't point me in any useful direction. Is there a way that I can redo the distro upgrade, only this time, allow it to overwrite my config file? I bet an alteration to the gdm.config file is to blame, but I have no idea what it is.

Here's the message:
Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
[Yes | No]

If you select yes, you get a bunch of stuff telling what version you are using. Further down, there is a message:

/usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: _glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module GLCore (loader failed, 7)

Any thoughts? As a newbie to all of this, would I just be better off using Knoppix or something to load an OS and then pull my data off (less than 10 megs - it's all text). Then I could just do a fresh install with Edgy.

---

### Post by gantww on 2006-11-13
Ok,
I fixed it, but it still isn't quite right.

I got to a command prompt and typed:
sudo apt-get install xserver-xorg-core

Then I rebooted. I got the login greeter, but no status during boot like I get on my other machines. Is something else whacked?

I got a notice that there were 23 packages awaiting upgrade. I tried to upgrade them, but it said not all of them could be installed. It then suggested a distro upgrade. I figured "what the heck", so I'm trying it.

---

### Post by PPAAUULL on 2006-11-13
Ok what you can do to get it right is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` That will allow you to reset the drivers for the display.

---

### Post by gantww on 2006-11-13
A final update. Everything works, except for the boot status stuff (the visual indicators that things are loading). I'm guessing that I got a bad version of xserver and that the reinstall fixed it. Does anyone have a guess?

---

### Post by PPAAUULL on 2006-11-13
When you reinstalled it reconfigured which is probobly what fixed it. does the same thing as the command I gave you.

---

### Post by gantww on 2006-11-13
I tried the following:
sudo dpkg-reconfigure -phigh xserver-xorg

Now my screen resolution is 640X480 now. I'm on an Inspiron 1100 laptop. What do I do now?

---

### Post by gantww on 2006-11-13
[How come there isn't a smiley character representing that moment of clarity you have right after posting something dumb...?]

I had to go back and edit xorg.config. Doooh! I need to go to bed and stay away from the computers for a while.

---

