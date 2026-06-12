---
title: "blank screen with mouse after i try and login"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by DesertFox on 2006-08-04
after i type the username and password i get a blank screen with a mouse it just sits there after that and does nothing, rebooting does'nt help

---

### Post by cantormath on 2006-08-04
> **DesertFox said:**
> after i type the username and password i get a blank screen with a mouse it just sits there after that and does nothing, rebooting does'nt help


and idea would be to hit 
<ctl>+<alt>+F1, login to terminal and read the logs.
to get back to gui, 
ctl>+<alt>+F7


another idea would be to kill/restart the gdm (gui) by hitting
<ctl>+<alt>+<bk Sp>
see what happens.

I would read the logs.

---

### Post by steve.horsley on 2006-08-04
Alt-Ctrl-F1 and log in to see the logs is a good start. While you are in the text console, you could also try setting up the X configuration by hand. Firstly, make a backup of the X configuration file like this:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

So that if the reconfiguration goes wrong, you can retrieve the existing configuration with the command:
> sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Now you can try to reconfigure the X server with this command which asks lots of difficult questions and then overwrites xorg.conf:
> sudo dpkg-reconfigure xserver-xorg
then restart the X server with this command:
> sudo /etc/init.d/gdm restart

Good luck.

---

### Post by DesertFox on 2006-08-04
hmm ok tryed that and i think i did everything right but it did'nt work, i am a total noob and trying this just kinda randomly i would reinstall but i am more intrested in learning how it works so thanks for your help

---

### Post by Hawkeye004 on 2008-07-10
Thanks for the advice, worked first try. Now I have to reconfigure my advanced desktop settings.

---

