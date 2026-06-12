---
title: "How install LG 19&quot; flat-panel monitor?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-06-15
[update] This is a widescreen monitor:  L196W

The monitor is working, but says optimum levels should be:

Resolution: 1440 x 900
Frequency: 60Hz


The 'Screen Res' box in Preferences doesn't give these options.

Screen currently set to: Res = 1024x768 / Freq = 75 Hz

---

### Post by annda on 2007-06-15
what is your video card? driver? laptop or desktop? what was your earlier monitor?

---

### Post by Killtown on 2007-06-15
I got monitor to work after rebooting.

---

### Post by Killtown on 2007-06-15
I have minor RES problem now.  See above.

---

### Post by Gmbrdilos on 2007-06-15
videocard make and model info would greatly help to the solution

---

### Post by Killtown on 2007-06-15
ECS board, integrated.

---

### Post by Killtown on 2007-06-15
Found this thread (#6):

Getting 1440x900 resolution
[http://ubuntuforums.org/showthread.php?t=370204&highlight=1440x900](http://ubuntuforums.org/showthread.php?t=370204&highlight=1440x900)


Not sure how to do this.  Can someone guide me through it?

---

### Post by Killtown on 2007-06-15
Following that poster's instructions.  Not sure about this part:

> Copy all of that, and paste it into your xorg.conf file (sudo gedit /etc/X11/xorg.conf), in the monitor section, save the file. Then Alt+F1
"Alt+F1" just opened my applications pop-up box. Was it supposed to open up the terminal or something?

[Solved]Hit Alt+**F2**!

---

### Post by thenixedreport on 2007-06-16
Is there a graphical way to do this out of curiosity?  I know that PCLinuxOS allows you to change the monitor type.  Does Ubuntu have a similar utility?  I'm not running 7.04 right now, so I wouldn't be able to find out myself.

---

### Post by Killtown on 2007-06-27
Still having trouble setting my screen resolution.

Trying to get it to this:

Resolution: 1440 x 900
Frequency: 60Hz

See above for all that I've done so far.

---

### Post by ckempo on 2007-06-27
> **Killtown said:**
> Following that poster's instructions.  Not sure about this part:


"Alt+F1" just opened my applications pop-up box. Was it supposed to open up the terminal or something?

Try this instead.

Hit Alt+F1
a window will appear for you to type a command into. Enter the following here:
  gksu gedit /etc/X11/xorg.conf

gedit should open, with the file open for editing.

Now, follow the guide **very carefully** and make any required changes. Then save the file and exit gedit.

Then reboot (or, hit CTRL+ALT+BACKSPACE together)

See if that works.

---

### Post by CherenkovBlue on 2007-06-27
try this, open your terminal and run 

sudo dpkg-reconfigure xserver-xorg

it will ask you to pick your driver and stuff, so make sure you know what driver you're using. then pick your desired resolution when it asks you to

then you can run

sudo gedit  /etc/X11/xorg.conf and add the resolution you want next to all the other resolutions


Edit: xserver will need to be restarted, you can just reboot your machine.

---

### Post by CherenkovBlue on 2007-06-27
> **ckempo said:**
> Try this instead.

Hit Alt+F1
a window will appear for you to type a command into. Enter the following here:
  gksu gedit /etc/X11/xorg.conf

gedit should open, with the file open for editing.

Now, follow the guide **very carefully** and make any required changes. Then save the file and exit gedit.

Then reboot (or, hit CTRL+ALT+BACKSPACE together)

See if that works.

alt+F2

---

### Post by Killtown on 2007-06-27
> **CherenkovBlue said:**
> alt+F2
Yep, that did the trick!

---

### Post by ckempo on 2007-06-28
> **CherenkovBlue said:**
> alt+F2

Haha! Always helps when you give advice that you check it works first! Good spot, thanks for pointing that out.

---

