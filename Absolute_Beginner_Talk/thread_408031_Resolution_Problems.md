---
title: "Resolution Problems"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2007-04-12
I know I am capable of running a higher res than 1280x1024 but even editing the xorg.conf wont allow me to modify the resolution shown under the "Screen Resolution Preferences" program. I know to ```
gksudo gedit /etc/X11/xorg.conf
``` but it does nothing. How can I use 1400x1050/1600x1200 or at least delete some of the useless ones like 800x600?

Thank you.

---

### Post by Gazneth on 2007-04-12
I had a similar problem when I screwed up an ATI driver configuration to run Beryl, I reconfigured X which seemed rather extreme to me but it worked to re-enable all my widescreen resolutions. Be careful doing this but if it does mess up you can run through the process by booting to the recovery console.
To start boot to the recovery console
```
sudo dpkg-reconfigure xserver-xorg
```
to restart X
```
startx
```
When in the X configuration dialog there is a screen where you can enable the various resolutions that your setup can handle.  Good Luck.:D

---

### Post by Skidlz on 2007-04-12
Good idea. I have done that in the past and had it work but now it seems to do nothing at all except over-right some options that make beryl work. Luckily I found [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Mandriva](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Mandriva) and it saved me. I guess 1280x1024 is ok.

---

### Post by freebird54 on 2007-04-12
Sometimes the 'high' end of resolutions available is apparently constrained by what the x system thinks of your monitor's capabilities.  If it has your monitor as stopping a 75 or 85 refresh rate, it might not think that 1440x### or 1600x### is an option.  Make sure the HorizSync and VertRefresh entries are in your Monitor section of xorg.conf - AND CORRECT FOR YOUR MONITOR!  (keep the magic blue smoke inside the monitor!)

My setup will do 1600x1200 - but I run it at 1280x1025 for higher refresh rate (85) and font size (old age) reasons...

My monitor section:  (numbers from the manufacturer - "best" resolution is 1280x1024 @85Hz)

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection
```

Hope it helps!

---

### Post by Skidlz on 2007-04-13
still no dice. Im not sure the problem even gets so far as the config file. The screen resolutions under system>preferences>screen resolution show some resolutions that are not in the xorg.conf file and is also missing some from it. The over lap of them is only chance. Thanks for all the input!

---

### Post by freebird54 on 2007-04-13
I had that problem a few times - but I got them much more in sync by running the following

```
sudo dpkg-reconfigure xserver-xorg
```

with the GUI shut down.  Now all I have is one entry I didn't choose :)

If you want to try that - I can post a few pointers on how to get through it unscathed...

---

### Post by Skidlz on 2007-04-13
well I tried it *again* still with no luck. This time I ran sudo init 1 to stop the GUI. I don't know if I should have done that but it seemed to have the exact same results as running with gnome running. Since dpkg-reconfigure wont work, is their any work around? Something like gconf-editor?

Thank You All.

---

### Post by freebird54 on 2007-04-13
What did you answer about the monitor section of questions?  Did you choose 'medium'?  That seems to be the simplest of the 'auto-detect' methods...

You toggled ON all the resolutions you want, and OFF all the ones you don't?

Of course you did - I'm just grasping at straws here...

What ARE the specs of your monitor?  What resolution are you trying for?  You never know what might trigger a thought - so the more info the better!

---

### Post by Skidlz on 2007-04-13
I totally agree. Even unrelated thoughts can help. But, yes, I checked on the resolutions I wanted and off the ones I didn't. Instead of medium I think I chose easy as the monitor selection.  For whatever reason, my previous instillation of 6.10 allowed higher resolutions and frequencies. Sadly once I reinstalled It went from something like 1400x1050 @72Hz down to my current 1280x1024 @50Hz.

---

### Post by freebird54 on 2007-04-13
Might be worth a try with medium - last time i did that it gave me resolutions higher than I wanted - and I had to restrict them down with xorg.conf entries...

Are you using a different version of the video driver this time?

---

### Post by Skidlz on 2007-04-13
I feel foolish. I don't even know the name of the driver to check the version. I know it is nvidia and not the legacy driver but that is all. Even if I knew what it was now I still wouldn't know what it was. I will try Medium now. Thanks.

---

### Post by Skidlz on 2007-04-13
I was almost sure that would work because of the Highest Resolution setting under medium. Sadly, it still had no effect on the screen res. It did change several things in the xorg.conf file so it is saving the changes, just not recognizing them. I guess it's time to leave it alone. Thanks for all the help and ideas!

---

