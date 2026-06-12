---
title: "Xserver problem ubuntu 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Rephab on 2007-10-22
Hi, i've some strange problem with my graphic card.
First time i installed 7.10 everything worked fine (exept my X-Fi soundcard and the 8800 graphic card)... after that i installed the nvidia driver... everything ok.
After one reboot the system locks up when the xserver starts and a window appears telling me that is impossible to recognize my video card and asking me if i want to configure it or loading in a safe graphic mode.
Now... every choose i made locks up the system!

If i load the safe mode at GRUB menu and then, type "nvidia-xconfig" and "init 5" i'm able to run the gui.
At this time i've the screen in 640x480 mode, so i open the xorg.conf file and overwrite it with the old file that worked the first time i've installed the drivers.
After a Xserver restart i've the resolution i want with the nvidia drivers well-functioning and everything works.

Now.. if i restart the system in normal mode nothing change... i've the same flashing black screen and the same warning window.

I read some posts regarding xserver problems but nothing usefull.

Can anyone help me?

(sorry for my bad english :()

---

### Post by sugarland2k on 2007-10-22
If you can get to a command line terminal, you can try to rebuild your xorg server...

To reconfigure your X-Server
sudo dpkg-reconfigure xserver-xorg

This is a script to configure the xserver.  Mostly you can accept the defaults, unless you are aware of a keyboard or mouse requirement that is different than the default.  When you get to the display driver, choose "VESA" rather than the one for your graphics card.  When you get to the monitor, make sure to "x" the resolution that you want for your desktop.  Set the refresh range as appropriate for your monitor.  Finish the script, then type in "startx" and you should get a graphical desktop.  

(Stick with the defaults unless you know something is wrong)

Good luck - if this will not work, let us know!

---

### Post by sugarland2k on 2007-10-22
Try looking at 
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

A great website!

Billy

---

### Post by Rephab on 2007-10-24
I tried to reconfigure the X-server, i launched GNOME and no problems... then i installed the nvidia drivers and... *flash" *flash" *flash" :)

But i solved my problem with Envy.
I don't know what process this software does... it's certainly longer than nvidia installation process and more complex (for Linux noob like me :))
Thank you for your help!

---

