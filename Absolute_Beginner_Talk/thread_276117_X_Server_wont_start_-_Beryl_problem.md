---
title: "X Server wont start - Beryl problem"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-12
Cheers, 

I tried to install Beryl on my system by following the instructions given at
[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

but after doing all of the instructions and I restarted my pc, I get the message that X-Server wont start and then ubuntu brings me to text mode.  But when I typed in startx my desktop loaded.  But the problem is right now is that I have to go to text mode everytime I restart my pc and type in startx instead of just loading gnome automatically.

Also I did noticed that I already have a Gem icon on my menu, so I assume that Beryl installed fine but I noticed that the current window manager that it is using is metacity and not beryl.  I tried to select beryl but I just comes back with metacity.

Any idea on what my next step is???


*[size=1]Changed the title a bit*- Artificial Intelligence[/size]

---

### Post by delphiguy on 2006-10-12
also when I type beryl from terminal I get
$ beryl
XGL Absent, checking for NVIDIA
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Nvidia Absent, assuming AIGLX
beryl: No composite extension
$

And I have also removed these two line from my sessions->startup programs:
xmodmap -e "keycode 22 = BackSpace"
beryl-manager

but I still get the text mode.

What do I do now? maybe beryl is not for me so can I uninstall it?

---

### Post by whizbaby on 2006-10-12
Beryl is installed but not running. You can verify by clicking on the red gem and select beryl as a window manager. The screen will flicker a bit and then metacity will again be the WM in the gem's menu.
What is your graphics adapter? As the message says composite is not enabled.

---

### Post by delphiguy on 2006-10-12
Yep, that is what happening right now.
I have an NVDIA GeForce FX5200, so how do I enable composite then?

---

### Post by whizbaby on 2006-10-12
In /etc/X11/xorg.conf I have the options
in the nvidia driver section:

Option         "UseFBDev"   "true"
Option         "RenderAccel" "true"
Option         "AllowGLXWithComposite" "true"

just after the nvidia driver section:

Section "Extensions"
        Option  "Composite"     "Enable"
        Option "RENDER" "true"
        Option "DAMAGE" "true"
EndSection

Your card has best to be run with the (proprietary) **nvidia-glx** driver, is it installed? If not, do that first.
Being new to Beryl/Compiz and not knowing much about graphics drivers I don't claim the above to work for everyone or to make much sense, it's only the setting that made beryl work for me (on the nervous newt).

---

### Post by delphiguy on 2006-10-12
Ok I found my problem, and it seems to have fixed both of my issues, that X Server wont start and that Beryl wont work.

Here's what I did.  While I was editing etc/X11/xorg.conf I was just copy/paste from the article I mention above to gEdit and somehow when I pasted this line Option &#8220;RenderAccel&#8221; &#8220;true&#8221; the double quotes in true was changed into an ascii character which is not visible in gedit but is visible on vim.  So after fixing that, I restarted my pc and low-and-behold everything went back to normal.

And yes I did installed the nvidia-glx driver.

Thanks for your time and effort in helping me WhizBaby.

---

