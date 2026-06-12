---
title: "need help with 3D acceleration [GeForce FX 5900] (rev a1)"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by poohma on 2007-03-02
This problem is now fixed by changing nv to nvidia.

Ok, so I'm a noob...  

I have battled long and hard to get my newly installed ubuntu installation to work.
Now I'm fairly happy with the result, only 3D acceleration left, I hope.

To get this to work I had to try a lot of programs like envy, automatix and of course the nvidia drivers both from the site and through synaptics.

Fondeling around in the blind I have found how to set up the screen resolution.
To do that I had to manually edit my /etc/X11/xorg.conf file's horizontal and vertical rate to fit my monitor and not the default. 

Gnome freezes if I change driver to nvidia though...  is that the problem?
I just want 3D games to work and all else stay as it is :-) is it at all possible?
Is there any way to easily back up my settings? (I don't know what files I have changed)

From xorg.conf:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nv"
EndSection

Result of lspci|grep VGA:
01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900] (rev a1)

poohma@Darkblaze:~$ glxinfo|grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

poohma@Darkblaze:~$ uname -a
Linux Darkblaze 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Thanks for reading :-)

---

### Post by janz84 on 2007-03-02
did you do a 
```

sudo apt-get install nvidia-glx

```yet?

if not, restart your computer after it installs

---

### Post by poohma on 2007-03-02
Thank you for quick response!!! 

I wanted to change nv to nvidia one more time just to be 100% certain that I'd done it...
 LO AND BEHOLD! IT WORKS!
I don't know what I've been doing wrong before...  but hey...  still a noob.

And to answer you question: yes I tried that, dont remember what the last thing I used was but my money is on the brilliant program envy :-D

---

### Post by RomeReactor on 2007-03-02
Hi. Gnome freezing might be due to having the drivers you downloaded from the Nvidia site still installed; did you uninstall them?

**EDIT**: Oops, sorry. Too slow =)

---

### Post by janz84 on 2007-03-02
> **RomeReactor said:**
> Hi. Gnome freezing might be due to having the drivers you downloaded from the Nvidia site still installed; did you uninstall them?

**EDIT**: Oops, sorry. Too slow =)


only if they are a newer version than the ones in the repo

---

### Post by old_geekster on 2007-03-02
Hey poohma, try this guide:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

As a recent convert to U 6.10, I can tell you that this is the best.  I have used it numerous times.

Also, here is the best guide for installing programs that I have found:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I hope that these will make your experience as good as mine.

---

