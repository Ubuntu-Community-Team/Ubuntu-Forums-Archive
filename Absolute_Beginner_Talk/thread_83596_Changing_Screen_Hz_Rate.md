---
title: "Changing Screen Hz Rate"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by bumcheekcity on 2005-10-29
To cut a long story short, my version of Ubuntu Linux starts up in some resolution above 75Hz. I have a (rather gourgrous :D) Samsung 913N 19" TFT Monitor, and it doesn't like anything above 85Hz, and simply displays no output, and a warning to change the refresh rate back down to its native. 

I need a way of editing my installation of Ubuntu, in the command line, to load up at 1280x1024 at 60-75Hz. I'm very new to this stuff. 

Just to mention that it obviously loads the BIOS and command line fine, but when the (is it GNOME) graphical interface loads, it stops showing anything on my monitor because Ubuntu tries to use a refresh rate outside of 60-75Hz, and my monitor simply doesn't show them. 

All and any help, especially copy+paste lines of code for a newb to use, would be greatly appreciated :D Thanks

---

### Post by adwait on 2005-10-29
try running
```
sudo dpkg-reconfigure xserver-xorg
```
I think it allows you to set your refresh rate etc...........

---

### Post by stuporglue on 2005-10-29
Do you have a way to find it's vertical and horizontal refresh rates?

The file you'll want to edit is /etc/X11/xorg.conf. The section in this file is the "Monitor" section.

To edit it on the command line, wait till the screen goes black when Gnome starts, then hit ctrl+alt+F2. You *should* get a login screen. Login then go to /etc/X11 and make a backup file of your xorg.conf like this (you type the username/password, and the lines with $ in front of them):

username: joebob
password: joebob'spassword
$ cd /etc/X11
/etc/X11
$ sudo cp xorg.conf xorg.conf.backup
$ sudo nano xorg.conf

Try lowering the vertical refresh rate to a range your monitor likes. The shortcuts for nano (the text editor) look like this ^X at the bottom of the screen. ^ means ctrl. 

When you've saved, save (^o) and exit (^x), then type...
$ sudo /etc/init.d/gdm restart
$ exit

Type ctrl+alt+F7 to get back to GDM...hopefully. :-) 

Good luck!

---

### Post by bumcheekcity on 2005-10-29
Thanks stuporglue, I followed your instructions to the letter and they worked. Ubuntu was trying to use a refresh rate of 50-75 Hz, for some reason, so I've just changed that to 60-75Hz, and it loaded up GNOME brilliantly.

However, it loaded up GNOME brilliantly on 1024x768. This isn't bad (hell, at least it loaded up!) but the native for my monitor is 1280x1024. I can see that 1280x1024, 1024x768 and 800x600 are all in the xorg.conf file, in the bit just under the edit for the Refresh Rate. HOWEVER, I can only select a maximum of 1024x768 on the GNOME Screen Resolution thingy. Is there something else I need to do to enable this?

---

