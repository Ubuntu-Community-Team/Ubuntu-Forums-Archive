---
title: "Widescreen and mouse buttons"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by UberNero on 2007-03-02
Hello, just installed ubuntu 6.06 on my desktop, Had enough of windows crashes so i decided to try something new,  Now heres my problem, Already got most of the basics sorted out, updated nVidia drivers, flash player installed, the small stuff, however right now im stuck with 2 things ive got no clue how to fix
1, Im using a 19inch 1440x900 widescreen monitor, and the resolution settings only go up to 1024x768, its really starting to bug my eyes and was wondering if there was a quick fix to this problem,  Video card is a 7600GT 256mb PCI-e using DVI cable.

2. Not as major as the first, but my mouse has 2 side buttons, its a logitech wireless, and i used them before for the forward and back keys in firefox, now they do nothing in ubuntu, anyone know how to fix that?

Thanks for your help, And if you do try to help, remember im new to linux so step by step and detailed would be much appreciated.

---

### Post by o_fortuna on 2007-03-03
If you have the nvidia drivers installed, try this (I think it should work)

Press Alt+F2 to open up the run command and type this:
```
nvidia-settings
```

This should bring up the nvidia X server settings. On the X Server Display Configuration you should be able to select the video mode.

If that doesn't work, you should first look up the vertical and horizontal refresh (sync) rates on your monitor. When you've done that, open up a terminal (Applications--Accessories--Terminal) and type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You'll get a bunch of questions. Be sure to have nvidia (not nv) set as your video driver. Select Advanced when you get to the monitor part and put in your refresh rates; be sure to tell it to save those values to the configuration.

And then that should work. About your mouse problem, I'm not quite sure. Does [this]("http://doc.gwos.org/index.php/Logitech_mice_dapper#Part_2:Side_buttons_and_Nautilus.2C_Epiphany.2C_Firefox.2FOpera_.28Optional.29") help?

---

### Post by Amenemhet on 2007-03-03
Ugh, nice video card (turns a bit green) but to help you I should imagine you need the drivers for both, check the manufacturer's website. They may have a driver you need to install for linux etc.

---

### Post by shaft350x on 2007-03-03
There are likely to be several threads on both of these topics, I've been more successful as far the mouse buttons are concerned, I haven't messed too much with my screen resolution.  I am not sure if these are exactly the how-to threads that I used to get my mouse buttons working but I think they will work for you.

[http://www.ubuntuforums.org/showthread.php?t=327131&highlight=mouse+buttons](http://www.ubuntuforums.org/showthread.php?t=327131&highlight=mouse+buttons)

And a more complicated and in depth thread

[http://www.ubuntuforums.org/showthread.php?t=246770&highlight=mouse+buttons](http://www.ubuntuforums.org/showthread.php?t=246770&highlight=mouse+buttons)

---

### Post by UberNero on 2007-03-03
Ok, so that didint work, sudo dpkg-reconfigure -phigh xserver-xorg gave me a screen in the terminal that looked like DOS with a selection of screen resolution, went down to 1440x900 and hit enter, window closed and nothing happened, also nvidia-settings opens, but theres not settings in it that i can change

also couldnt get the official nVidia linux driver to install, got a coding error when it tried to install, so i Used some sudo code thing to download and install it, now im not sure if that worked.

---

### Post by Aliarse on 2007-03-03
This is how i managed to get 1440x900 on my LG Flatron 19" Widescreen

[http://ubuntuforums.org/showthread.php?p=2232359#post2232359](http://ubuntuforums.org/showthread.php?p=2232359#post2232359)

HTH.

---

### Post by UberNero on 2007-03-03
It wont let me save it after i change it, gives me
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

---

### Post by Aliarse on 2007-03-03
In a terminal, type ```
sudo gedit /etc/X11/xorg.conf
```, it might/should ask you for your user password before it allows it to open.

Sorry bout that, i just added it to the post in the thread above.

---

### Post by o_fortuna on 2007-03-03
> **UberNero said:**
> Ok, so that didint work, sudo dpkg-reconfigure -phigh xserver-xorg gave me a screen in the terminal that looked like DOS with a selection of screen resolution, went down to 1440x900 and hit enter, window closed and nothing happened, also nvidia-settings opens, but theres not settings in it that i can change

also couldnt get the official nVidia linux driver to install, got a coding error when it tried to install, so i Used some sudo code thing to download and install it, now im not sure if that worked.
Ack! My bad. You have to press the space bar to select something in the reconfigure thing :)

If you have an nvidia card, you want to install it through synaptic package manager. Just look for nvidia-glx (if it's green then it's already installed). Then run
```
sudo nvidia-xconfig
```
in a terminal, which will set you up. Log out, press Ctrl+Alt+Backspace, and then log back in. That should set it up for you.

Also, you should type
```
gksudo gedit /etc/X11/xorg.conf
```
You shouldn't use sudo when running graphical applications

---

### Post by UberNero on 2007-03-03
Woot, it works now, thanks for the help, my eyes thank you
Now to get wine running and some media players running and im all set, Should be a fun day.

---

