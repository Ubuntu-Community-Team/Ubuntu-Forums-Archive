---
title: "New install and usual problems"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by thepocketdrummer on 2007-05-01
I have previously installed different version of Ubuntu, and each build seems to self destruct. I use it for a while, and suddenly things stop working. Error messages pop up... so again, I'm to the point where I can't fix it and I just want to reinstall.

That said, I lost the little paper I kept from the first time I tried to install. I'm using an Athlon 64 3700 and a nVidia 7800 GT video card. For some reason, after Ubuntu installs, the GUI doesn't come up, just a solid color background. I know I have to change it to vesa for it to show up, but I forgot all of the other things necessary during the initial installation.

So, my questions are as follows:

1. How do I change to vesa (I forgot all the commands)?
2. How do I get my multimedia keyboard to work properly (mainly the music controls. mute/pause/play/volume)
3. How do I get my Logitech G7 mouse buttons to work as they should (front back buttons mainly)
4. How do I install the correct nvidia drivers?
5. How do I make the computer boot from the windows boot loader?
6. Is there anything else I can do to ensure this install doesn't mess up like the others?

I know it's a lot to ask, but if you guys could help me with this I would GREATLY appreciate it.

:guitar:

---

### Post by thepocketdrummer on 2007-05-01
Also, I forgot to mention. Is it better to get the 64-bit version or the standard?

---

### Post by knightnet on 2007-05-01
I don't think you need vesa. Boot to safe mode and directly install the nvidia binary drivers. That should be enough to get you going I think - I don't think you should need to reconfigure xorg.conf. I had the same problem when installing my desktop with a 7600GS.

On my MS keyboard, the extra buttons just work. Though I use KDE. You can reconfigure using the KDE settings for the keyboard.

For the mouse buttons, change the mouse section of /etc/X11/xorg.conf to:
```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse_Logitech"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option           "Resolution" "800"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```4 - "sudo aptitude install nvidia" ;) See 1

5 - Tilt!

6 - Dont mess? ;) [INDENT]     Actually, I've already broken my sound so I probably shouldn't comment here!
    OK, I will anyway! I keep notes on everything I install and configure (I keep a text file on the desktop and a more comprehensive set of information in a TiddlyWiki file). I also keep a copy of every amended config file, most especially:[INDENT][LIST]
[*]   sources.list
[*]   xorg.conf
[*]   26-hiddev.rules (contains my settings for my APC UPS)
[*]   apcupsd.conf (as above)
[*]   fstab
[*]   smb.conf[/LIST][/INDENT]- In fact, it is might even be better to delete the originals of these and create links to originals in your home folder. You then know where everything is that you've changed and can back them up very easily.
[/INDENT]Finally, I think that the standard install is safest unless you really want to go round recompiling most of your applications and drivers (and if you do, not only should you seek medical advice, you should head over to the Gentoo distribution which is likely to be more suited!).

PS: I'm fairly new at this Linux stuff myself so I hope I've got most of the above right.

All the best,
Julian.

---

