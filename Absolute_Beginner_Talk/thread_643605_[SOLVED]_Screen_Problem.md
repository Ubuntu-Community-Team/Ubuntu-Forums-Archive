---
title: "[SOLVED] Screen Problem"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by dsmorgan6922 on 2007-12-18
I tried to setup dual monitors with my T61 Laptop (Nvidia Quadra NVS 140M). In the process I really screwed up my screen settings and of course forgot to save the original configuration. 

Now my screen on my laptop isn't back to the right size and I've tried messing around with the Screen options to no avail. Is there some utility I can run to just reset everything to the original install screen configuration?

Thanks,
Doug Morgan

---

### Post by mmb1 on 2007-12-18
Have you tried ctrl-alt-backspace? Sometimes that randomly works for unknown reasons.

---

### Post by dsmorgan6922 on 2007-12-18
Yeah, restarting the xserver didn't help. I have restarted many, many, many times.

---

### Post by mmb1 on 2007-12-18
And you've already tried messing with the screen configuration options in preferences-screen resolution?

---

### Post by dsmorgan6922 on 2007-12-18
Yeah the problem is I don't know what the default one was and everthing I'm trying isn't what I had. Right now I'm running in 1280x800 but I know I was at 1400x1050. I tried setting it to that but when that happens I just scroll the screen around (like when I move the mouse to the ends of the screen it scrolls to another portion that wasn't viewable)

---

### Post by mmb1 on 2007-12-18
Alright, you keep on tinkering with different resolutions, I'm going to see if I can find either a solution or a utility like the one you mentioned that will reset the resolution to what it was before.

---

### Post by RomeReactor on 2007-12-18
Hi. Try looking in **/etc/X11** for backups of the xorg.conf file:
```
ls /etc/X11
```

You should see some xorg.conf files with numbers at the end; for example, here's what my /etc/X11 folder directory like:
```
app-defaults             xorg.conf~                Xresources
cursors                  xorg.conf.1               xserver
default-display-manager  xorg.conf.20071005162034  Xsession
fonts                    xorg.conf.20071005162055  Xsession.d
rgb.txt                  xorg.conf.20071005162104  Xsession.options
X                        xorg.conf.20071005162138  XvMCConfig
xinit                    xorg.conf.20071015222625  Xwrapper.config
xkb                      xorg.conf.failsafe
xorg.conf                xorg.conf.failsafe.bak
```

As you can see there's a file named **xorg.conf~**; this is the most recent backup. Files that read like this:
```
xorg.conf.20071005162104
```
are older backups. You read them as: year/month/day/hours/minutes/seconds. Now, let's say I want to restore my xorg.conf using that particular file, saved on October 5th, at 4:21 PM (16:21, with 04 seconds):
```
sudo cp /etc/X11/xorg.conf.20071005162104 /etc/X11/xorg.conf
```
Now log out and back in. That should restore your xorg settings.

If the above doesn't work for you, you can reconfigure xorg. For that, you need to switch to a terminal by pressing CTRL+ALT+F1. Then, stop GDM:
```
sudo /etc/init.d/gdm stop
```
and then reconfigure X:
```
sudo dpkg-reconfigure xserver-xorg
```
If you're using the proprietary nVidia drivers, choose **nvidia** when asked to select which driver to use; otherwise accept all the defaults unless you're certain you need to change something, like the keyboard or mouse settings. When you're done reconfiguring, you should be brought back to your graphical desktop automatically; if not, run:
```
sudo /etc/init.d/gdm start
```
or reboot:
```
sudo reboot
```

Hope this helps.

---

### Post by erginemr on 2007-12-18
I do not know ins and outs of using dual monitors, but normally one can reconfigure the screen with the following console command:
```
sudo dpkg-reconfigure xserver-xorg
```

But before this, make a copy of your original config file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

You can also try playing with the graphical config applet "Screens and Graphics" under Main Menu -> System -> Admin, if you haven't done already.

If none of the above work, please post your xorg.conf file here, so that I (or another forum member) can comment on it. Please also inform us about the brands of your graphics card and monitors.

---

### Post by dsmorgan6922 on 2007-12-18
Thanks for all your help everyone I got it working. What I did:

1) Booted off the original Ubuntu disk and copied down the screen settings that worked off the boot disk

2) Reconfigured the gdm via what romoreactor said

3) Works!

Thanks a lot.

Doug

---

