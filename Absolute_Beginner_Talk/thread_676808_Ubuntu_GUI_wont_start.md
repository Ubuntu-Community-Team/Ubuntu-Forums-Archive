---
title: "Ubuntu GUI wont start"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by GnomeFoot on 2008-01-24
I was using the latest nvidia drivers (cant remember what they are called) and I installed the nvidia-setup/support or what its called. and uninstalled the nvidia drivers. now when I reboot the GUI wont start. how do I uninstall the nvidia-setup and reinstall the nvidia drivers? I guess that is whats wrong.

---

### Post by mikeyphi on 2008-01-24
> **GnomeFoot said:**
> I was using the latest nvidia drivers (cant remember what they are called) and I installed the nvidia-setup/support or what its called. and uninstalled the nvidia drivers. now when I reboot the GUI wont start. how do I uninstall the nvidia-setup and reinstall the nvidia drivers? I guess that is whats wrong.

Try this:
Open a terminal and enter:
sudo dpkg-reconfigure xserver-xorg

you will get a few pages of text with questions - accept the default answers - unless you know better!
When it's all done reboot your system - you might need to use the System/Administration/ Restricted Drivers Manager to reset the correct driver.

---

### Post by GnomeFoot on 2008-01-24
but I wont even get to the loginwindow. Grub -> Ubuntu -> then it goes black with "username: " but it blinks and I cant write anything. when I start to write it blinks and goes back to the same screen. Good explanation :confused:

---

### Post by scizzo on 2008-01-24
he means hitting Ctrl+Alt+F1 and do the command.

Or go to the recovery mode and move the xorg.conf you have or change the driver in there to "nv" and then restart.

---

### Post by Joeb454 on 2008-01-24
How do you mean it blinks? The screen blinks or the cursor blinks?

I've had that before, but I still managed to log in to run the command in post #2

---

### Post by GnomeFoot on 2008-01-24
The screens all black with the "login: " row. the whole screen blinks, like it restarts.

---

### Post by NiceGuy on 2008-01-24
When booting up, try selecting the 'recovery mode' option in GRUB (second one down). This should give you a root prompt and from there you can try  try running dpkg-reconfigure xserver-xorg.

---

### Post by limac on 2008-01-24
GnomeFoot: try reconfiguring X through thru a command prompt  (Ctrl + Alt + F1 or F2 or F3 ... F6) and F7 will be the GUI version of it! 

and see how that goes

regards,
limac

---

### Post by philinux on 2008-01-24
Go into recovery mode and use this

ls -l /etc/X11
This will list the contents of the X11 directory and show the date time etc.

Make sure of the capital X

Look for files xorg.conf and xorg.conf~

the one with the ~ could be the backup. Check the date/time stamp.

If it is then

cp /etc/X11/xorg.conf~ /etcX11/xorg.conf

This will restore the graphics/other config file.

---

### Post by limac on 2008-01-24
And also try what NiceGuy suggested

regards,
limac

---

### Post by GnomeFoot on 2008-01-24
Thanks for all the replies, will try it as soon as I get home from work

---

