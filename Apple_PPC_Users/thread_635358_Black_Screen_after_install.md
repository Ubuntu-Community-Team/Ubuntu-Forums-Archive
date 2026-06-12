---
title: "Black Screen after install"
date: 2007-12-08
forum: Apple PPC Users
---

### Post by ricolinux on 2007-12-08
I installed Gutsy 7.10 PPC on a Blue and white MAC G3 I run the installer to its full completion  and it found my Network and my hardware but when I reboot after finishing installation I get the USPLASH 
Screen and a "OVER RANGE" message on my monitor I tried several solutions I found in the forums to no avail.
I can run the console and login using the user name  and password that I setup during installation.
I've installed Ubuntu and othe flavors of Linux for over 2 years I have a home network with 3 ubuntu boxes and 4 XP (I need Adobe and other programs for my business) I'm not afraid to use the TERMINAL I enjoy the challenge and I use quite often.
This G3 Mac was destined to the recycle pile so I rescued a year ago and only just last week I found the time to work on it.
Never had a problem setting my monitors either on Linux or XP so if anybody has some time to show me the steps to set this puppy up I want to turn my friends with old Macs to UBUNTU.
Thanks
Ricolinux

---

### Post by ricolinux on 2007-12-09
I guess I should tell my clients to stick by Microsoft, It seems the linux world is only for the elite gearhead us mere mortals , poor users should stay with  the INTEL/MS Machinery.
I had the opportunity to convert dozens of teachers to UBUNTU but with this type of support I rather not.
These people are used to the GUI of their systems.
I'll keep my single Ubuntu box just for kicks.
Thanks anyway :(  :confused:  :mad:  :guitar:

---

### Post by 3rdalbum on 2007-12-10
First advice: Wait longer before giving up. The best person to help you might be sleeping or working at their day job.

Second advice: In future, link to any articles that you've read and tried, if possible, because some older articles might not still be relevent, and we'll know at least what you've tried.

Third piece of advice: Go to the terminal (press Control-Option-F2), log in, and then type:

```
sudo dpkg-reconfigure xserver-xorg
```

Accept the defaults that it gives you, until you get to the question about monitor autodetection. Select "No" for that. 

You will be asked to select some resolutions - select only the bottom 3.

You will be asked if you want "Simple", "Medium" or "Advanced" manual setup. Try simple first; that's where you select the size of the screen.

After the program has finished, type:

```
sudo reboot
```

If you get the same problem happening, do it again and try the Medium setting; try different (reasonably-low) modes, unless you happen to know the monitor's native resolution (if on an LCD). Reboot.

If that doesn't work, go to the manual for the monitor and find where it says the "Horizontal Sync" and "Vertical Refresh" (or something similar). Then use the Advanced mode of setup to put those values straight in. Don't put in any special characters other than the hyphen - they should be put in something like:

```
80-112
```

Try all that; if it still gives the same problem, please post back here.

---

### Post by ricolinux on 2007-12-10
Thanks 3rdalbum for your reply and your right I'd waited a while before ranting, I'm not giving up on Ubuntu It just make cranky when I finish installing  it and the only way I an use it its thru  the command line.
I followed your instructions to the letter and still get the OVER RANGE screen  oh BTW I re-installaed  a new copy of DEBIAN 4 when  I press CTRL+F7 I can almost see the desktop login for a brief moment. when a I run STARTX  it says the server is already active for display 0
If this server is no longer running , remove /tmp/.X0-lock and start again
followed by
Xlib: connection to ":0.0" refused by server
Xlib Invalid MIT-MAGIC-COOKIE-1 key
giving up
xinit:unable to connect to X server
xinit: No such process (errno 3): Server error
I really wanted to fix this computer to give it to a local family that can't afford to buy a regular computer.
Thanks 
for your efforts 
Regards 
Ricolinux

---

### Post by Auria on 2007-12-10
-removed-

---

