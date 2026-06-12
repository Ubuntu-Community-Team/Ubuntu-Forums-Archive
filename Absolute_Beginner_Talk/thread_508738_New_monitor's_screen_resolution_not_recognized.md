---
title: "New monitor's screen resolution not recognized"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-07-24
I want to use my new monitor's 1280x1024 screen resolution, but the highest listed under system > pref > screen resolution is 1024x768.

What do I have to do? I imagine this has something to do with xorg.conf but I'm pretty much clueless...

---

### Post by rogueluke on 2007-07-24
Your graphics driver might not be supporting that.  I installed the nvidea-setting stuff posted on [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04) and was able to get all my monitors working.

---

### Post by benfindlay on 2007-07-24
type ```
sudo dpkg-reconfigure xserver.xorg
``` into a terminal and follow the on screen instructions. When you get to the bit which lists different resolutions scroll up and down with the arrow keys and use spacebar to tick the different options you want enabling!

Hope this helps!

---

### Post by phoenix23 on 2007-07-24
Ran into a BIG problem, guys...

I was messing around with nvidia-settings and set it to 1280x1024, and now I get a black screen after the loading page with the orange bar. The login screen works (i can hear the login sound) but I don't see anything...

How can I reset the GUI so I can do what you guys just said? I can't get to a terminal with a blank, black screen. Will I have to reinstall the drivers?

---

### Post by punx45 on 2007-07-24
hitting ctl+alt+F1 should get you into a terminal.
or possibly alt+F1 (havent used gnome in a while)
you can then do your fixes, restart GDM, and return to the GUI by hitting (ctl+)alt+F7 (pretty sure)

after you do that go into /etc/X11 make a copy of xorg.conf, and call it xorg.conf.mysettings (or whatever).   next time you bork your settings you can just revert back to the mysettings xorg.conf.

---

### Post by phoenix23 on 2007-07-24
Thanks.

I used ctrl alt f2 to get to a terminal, and I entered sudo dpkg-reconfigure xserver.xorg but it says that the package isn't installed.

Is there  a way just to edit the xorg.conf file so I can take out the 1280x1024, and go back to the old one? Or should I try to reinstall my nvidia drivers?

Still stuck at the black screen...

---

### Post by punx45 on 2007-07-24
if the nvidia-settings program was responsible, it may have created a backup before it edited your xorg.conf.   are there any xorg.conf files labeled as backups, or with a string of numbers that look like a date? if so you can cp them to xorg.conf and restart GDM to get back to where you began.

otherwise you might be able to successfully edit the existing xorg.conf file.   changing the driver to vesa or the generic nvidia (forget the name) might help.

---

### Post by phoenix23 on 2007-07-24
I'm not sure if there are any backups. How might I look?

the xorg.conf looks like it's still using my old ATI graphics card... it's weird because I can still see the startup screen with my monitor plugged into the new graphics card... So what should I change?

---

### Post by benfindlay on 2007-07-24
in the terminal you can type ```
sudo nano /etc/X11/xorg.conf
```

this launches nano (a terminal based text editor). You can delete references to the resolutions you want rid of through this. Then press ctrl+x to exit, pressing > Y to save when prompted and pressing > enter to over-write the filename.

Then a reboot should be all you need!

Hope this helps!

---

### Post by phoenix23 on 2007-07-24
Ok, I removed the resolutions, but it still has a black screen...

Also tried reinstalling nvidia

---

### Post by alienexplorers on 2007-07-24
Have you tried using the Envy scripts and the once its working using a modeline in you monitor section to get the resolution you want.  Modeline generator is located at: > [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by punx45 on 2007-07-25
go into /etc/X11 and do ```
ls -al
``` to see if there are any backups.   they may look like ```
xorg.conf.back
xorg.conf.22072007
```
or something else like that

also the dpkg-reconfigure that you tried before might have been missing some flags.   somewhere in the body of the xorg.conf it tells you to issue that if you are having problems. take a look and see.

view the file:
```
less /etc/X11/xorg.conf
```
search:
type '/dpkg' press <enter> and matching values will be highlighted.  press <n> to go to the next match of 'dpkg' if there is one.

you should find instructions to 'dpkg-reconfigure -??? xserver or whatever'

---

