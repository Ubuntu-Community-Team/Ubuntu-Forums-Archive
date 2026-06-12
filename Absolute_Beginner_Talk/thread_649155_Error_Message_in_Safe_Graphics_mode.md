---
title: "Error Message in Safe Graphics mode"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by smiths37 on 2007-12-24
When I try to install Ubuntu normally, I get the loading screen and then it goes to a blank black screen after a few minutes.
I checked the disk for errors- there are none.
I then tried installing in safe graphics mode.  I get an error message that says, "[FONT="Courier New"]Failed to start the x server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?"  [/FONT]
If I click yes, this is the message that I get: "/[FONT="Courier New"]etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning: Failsafe mode was already attempted within 30 seconds
Warning: Falling back to gdm to report the issue[/FONT]."
I click ok, because there is nothing else to do.  And I receive a message that says. "[FONT="Courier New"]The x server is now disabled.  Restart GDM when it is configured correctly."[/FONT]
I honestly have no idea what this means.  Can anyone give me some insight and/or suggestions on what to do?
Thanks!

---

### Post by Rocket2DMn on 2007-12-24
You will need to reconfigure the X-server, this happens sometimes when the video card is not immediately recognized by X (the backend of the GUI).  You need to get to a terminal and run the following commands - the first will stop gdm (GNOME desktop manager), the second will run you through a configuration which will ask you questions about your hardware, and the third will start gdm again.
Do your best to answer the questions about hardware - the very least you need to know what screen resolutions to use and what type of video card you have (select "ati" driver if your card is an ATI and select "nv" if your card is an NVIDIA).  Press TAB to move around and SPACEBAR to select.  You should select your monitor's highest resolution and everything less than that.
Hit CTRL+ALT+F1 to get to a terminal.
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by smiths37 on 2007-12-27
Thanks!  I will try this tonight!

---

