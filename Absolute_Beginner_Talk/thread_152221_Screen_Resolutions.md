---
title: "Screen Resolutions?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Charlatat on 2006-03-29
How does one add a screen resolution?  You know the monitor can support it, but the mode wasn't selected during install and now want to add it.  Any suggestions?

---

### Post by mlind on 2006-03-29
```

sudo dpkg-reconfigure xserver-xorg

```

accept all default values. Wizard should prompt about additional resolutions too,
so just enable what you need. Restart your Xserver, and log in. You should be able to
change default resolution from System > Preferences > Screen Resolution.

also Ctrl+ALT +  and Ctr+Alt -  will cycle through configured resolutions.

---

### Post by Charlatat on 2006-03-29
Ok, the wizard went fine, added the resolution I wanted.  However, when I'm in the Screen Resolution applet, the new resolution isn't listed.  What's up?

---

### Post by mlind on 2006-03-29
[QUOTE=Charlatat]Ok, the wizard went fine, added the resolution I wanted.  However, when I'm in the Screen Resolution applet, the new resolution isn't listed.  What's up?[/QUOTE]

did you restart your X server? try Ctrl+Alt+Backspace.
Also verify that your settings were stored on /etc/X11/xorg.conf

---

### Post by Charlatat on 2006-03-29
That worked, thanks!

---

### Post by dlhansen on 2006-03-29
When i run the xserve config it does not prompt me about screen resolutions. there is a sectiong on auto detect monitor settings and i accept the default value. after that the screen goes black and some text comes up and then i have to log back in. i assume that is the xserver thing starting up again. any ideas? thanks.

---

### Post by mlind on 2006-03-29
[QUOTE=dlhansen]When i run the xserve config it does not prompt me about screen resolutions. there is a sectiong on auto detect monitor settings and i accept the default value. after that the screen goes black and some text comes up and then i have to log back in. i assume that is the xserver thing starting up again. any ideas? thanks.[/QUOTE]

Well, you should answer 'Yes' to questions which say something about auto-detecting your hardware.
Especially on monitor autodetection.

---

### Post by dlhansen on 2006-03-29
I did and nothing happened. I have tried also editing the xorg file and adding the resolutinos according to instructions from other threads. still nothing. what am i donig wrong?

---

### Post by mlind on 2006-03-29
[QUOTE=dlhansen]I did and nothing happened. I have tried also editing the xorg file and adding the resolutinos according to instructions from other threads. still nothing. what am i donig wrong?[/QUOTE]

you shouldn't edit that file manually if you don't know what you're doing.

read carefully what that configuration wizard asks, then restart X server
if you made any changes. Does it say anything like it can't detect your monitor?

---

### Post by dlhansen on 2006-03-30
It detects it fine. Going through the setup menu does not ever give me the option to choose screen resolutions.

---

### Post by mlind on 2006-03-30
[QUOTE=dlhansen]It detects it fine. Going through the setup menu does not ever give me the option to choose screen resolutions.[/QUOTE]

well that's strange..

You can manually add resolutions too, but you need to know that your monitor can support those and that Hsync & Vrefresh rates
are correct.

configuration wizard doesn't show you screen like this?

---

### Post by MrFrodo on 2006-03-30
[QUOTE=mlind]```

sudo dpkg-reconfigure xserver-xorg

```

accept all default values. Wizard should prompt about additional resolutions too,
so just enable what you need. Restart your Xserver, and log in. You should be able to
change default resolution from System > Preferences > Screen Resolution.

also Ctrl+ALT +  and Ctr+Alt -  will cycle through configured resolutions.[/QUOTE]

I'm having this res problem on a brand new install. Where do I type this code? And what is Xserver?

---

### Post by mlind on 2006-03-30
[QUOTE=MrFrodo]I'm having this res problem on a brand new install. Where do I type this code? And what is Xserver?[/QUOTE]

You open a terminal and type it there. Applications menu, choose Accessories and then Terminal (for Gnome).

X Server is providing you the graphical environment you're probably looking right
now. I guess its right name is [X Windows System]("http://en.wikipedia.org/wiki/X_Window_System").

---

### Post by serlex on 2006-03-30
same problem here, at the minute im running my Ubuntu on 800x600. this resolution is TOO small to work on, i been trying to change this for a while now!
i would like to have at least 1024x768       

Monitor:Flatron L1720B
Graphics card: 440 64mb :(

i have tried 
```
sudo dpkg-reconfigure xserver-xorg
```

didnt change anything. can some help me plz

thanks

---

