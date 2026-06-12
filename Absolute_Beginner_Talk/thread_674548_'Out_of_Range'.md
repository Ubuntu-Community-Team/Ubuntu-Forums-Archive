---
title: "'Out of Range'"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by modnar58 on 2008-01-21
I'm new to Ubuntu and wanted to try out Linux for the first time and had a spare computer sitting around (Intel P4, Nvidia 6600GT AGP) that I'd try it out on.

Now the installation was very easy and quick (which is awesome) and at first I had no problem with it. After installation it booted up and I managed to get myself connected to the internet but after that I started to have a problem.

When I restarted my computer the splash/loader screen would show up with the progress bar but right about when it finishes loading the screen just goes hay-wire with colors and there is a box overlayed onto that that says "Out of Range." I have tried searching but haven't been able to find anything of help to fix it and some things that seemed like were fixes just seemed confusing to this newbie. 

All help very much appreciated!

---

### Post by chewearn on 2008-01-22
Boot into recovery mode; at the root prompt, run the following commands:
[INDENT]```
cd /etc/X11
cp xorg.conf xorg.conf.backup
nano xorg.conf
```
[/INDENT]
You will now be in nano text editor, move the cursor down until you reach the line:
Section "Screen"
Below that, you will find various screen resolutions.  Check to make sure there are no resolution that are too high for your monitor; if there is, delete it.

E.g. if you see "1600x1200", but your monitor support up to "1024x768" only, then delete all "1600x1200".

Press CTRL+X to exit the text editor (make sure to save your changes).  Then:
[INDENT]```
shutdown -r now
```
[/INDENT]to reboot.

---

### Post by LaRoza on 2008-01-22
Also, you could use:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

In recovery mode.

---

