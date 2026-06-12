---
title: "screen shakes"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by sdmtnbiker on 2007-10-27
I just upgraded to 7.10 and as soon as it rebooted the screen vibrates so bad its useless, if I kick the screen resolution down to 800x600 its ok. This is a Compaq Presario 2570US.
Help.

---

### Post by toddward on 2007-10-27
Have you adjusted the refresh rate on the monitor?  This is probably your bet to resolving the shaking of the image.

Try to get the refresh rate as high as it'll go.  It's a CRT, right?

---

### Post by sdmtnbiker on 2007-10-27
nope a laptop

---

### Post by toddward on 2007-10-27
> **sdmtnbiker said:**
> nope a laptop

Hmmm, please ensure that you have that screen set to 60hz.  Also, the **/etc/X11/xorg.conf** will have specific settings for this monitor.

More specically, a section that might look like this (for my monitor):

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

```

My advice is to look up for your laptops monitor what those values should be.  Once you input those values, you should have a non-flickering screen.  However, there may be deeper issues that I'm not aware of.  Keep me updated please.  

[COLOR="DarkRed"]BACKUP YOUR XORG.CONF FILE BEFORE ATTEMPTING CHANGES PLEASE![/COLOR]:)

As a note, when you update that file and save it (as root), Ctrl+Alt+Backspace will restart X.  If the changes don't work, you may be dumped back to a terminal with no graphics.  If this occurs, simply revert back to the backup.

---

### Post by sdmtnbiker on 2007-10-27
I am giving up, I have 2 of these laptops, same model numbers 2570US, 1 is running a dual boot w/XP and Ubuntu 7.10 no problems, but no matter what I do 7.10 on the other just dosen't work (screen resolution), It will run allthe others just fine, just not 7.10.   sigh   spent way to much time on this. Thanks for your help.

---

