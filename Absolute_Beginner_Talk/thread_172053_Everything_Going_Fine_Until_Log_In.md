---
title: "Everything Going Fine Until Log In"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by runnerguy11 on 2006-05-07
Hi,
I am totally new to Linux and I just installed it today on my 2001 iBook G3.  The install went smoothly and I wiped the hard drive clean.  The log in screen came up after install all clean and ready and I typed in my username and password which were correct.  Instead of showing the desktop it just stayed that brownish color and did not show anything else and I left it like this for 20 minutes.  I am able log in using terminal mode but I have no idea what to do with that.  How can I fix this?:confused:

---

### Post by nalmeth on 2006-05-07
hmm, not usual behavior.
Let's make sure you have the most recent/up-to-date packages in the ubuntu-desktop. Do you have an active internet connection?
If so, from the log-in screen, type CNTL-ALT-F2
log in as your user
type:
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade

Then reboot, and try again
sudo reboot

---

### Post by runnerguy11 on 2006-05-07
I did what nalmeth told me but when I logged into GNOME I still had the same problem.  Any more help would be greatley appreciated.

---

### Post by nalmeth on 2006-05-07
No error's when updating correct?
This seems to be a Gnome issue (the default ubuntu desktop environment),
but with the absence of other suggestions, you can try to change the video driver. 
Do you know what video card you have? If it's an intel integrated, the default driver should be i810. If it's an NVIDIA, the default will be nv. If it's ATI, the default is ati.
vesa is the driver we want to change to. You can go back and setup your video card later if you need 3D acceleration.
Log in with session type: failsafe terminal
type this command
sudo dpkg-reconfigure xserver-xorg
When you get to video driver selection, pick vesa
Pick the default's for everything else, unless you know better.

Other alternative's could be installing a different desktop evironment. If you have the space, you can try the kubuntu-desktop (alternative to gnome, prefered by many) or xubuntu-desktop (much lighter desktop, less features though).

To install them, use the failsafe terminal session (or the CNTL-ALT-F2 method) and type:
sudo apt-get install your_selection

Hopefully when you're successfully logged in you can figure out what is wrong with gnome.

Good luck

---

