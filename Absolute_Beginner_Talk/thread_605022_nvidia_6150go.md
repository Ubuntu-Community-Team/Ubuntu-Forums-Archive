---
title: "nvidia 6150go"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by t1hall on 2007-11-06
I'm having a small problem. I loaded Ubuntu Gusty on my HP Pavilion dv6000 (dv6119us) and everything went well. There was a problem though, when I connected a external monitor it messed up my Nvidia 6150go drivers. The question is, how do I reinstall this driver? When I go to my graphic card driver the correct driver is not listed.

---

### Post by Hospadar on 2007-11-06
the actual driver package is called "nvidia-glx" but I would bet the real problem is your x config file.  You should try doing a dpkg-reconfigure on your x server to set it up fresh.

before that though, did you install/use the restricted driver (which is the "nvidia-glx" driver)?  if you did, follow the next instructions exactly, if not, just replace "nvidia" with "nv"

first, let's get to a terminal Ctrl-Alt-F1 (Ctrl-Alt-F7 to get back to your GUI) now let's reconfigure X
```
sudo dpkg-reconfigure xserver-xorg
```
On the first screen of this dialog, select nvidia, then you can pretty much default through the rest of the options.  this should get you back to a good baseline of functionality.  there will be one page that has resolution options, you'll want to make sure your native resolution is selected here, other than that, just say yes and hit enter.
now restart the x server
```
sudo /etc/init.d/gdm restart
```
 now ctrl-alt-f7 back to your gui and see if it works!

**Note!**  you really should back up your xorg.conf file before you do any of this in case my instructions blow up your system (very unlikely) so you can at least be back to screwed up.  from a terminal:```
sudo cp /etc/X11/xorg.conf ~
``` this will copy the file to your home directory.

If things get mucky, start in recovery mode and copy the backup back to the original place```
sudo cp /home/<whatever your home directory is called>/xorg.conf /etc/X11/xorg.conf
```
when you're done,

---

### Post by t1hall on 2007-11-06
Steps 1 and 2 worked like a champ. Thank you very much. I do have one other question, and its not that important. How do I run Compiz on this laptop. I mean, I've had no problem with any other desktop, but this laptop has given me all kinds of trouble with trying to run Ubuntu. Gutsy was actually the first OS from Ubuntu that would run on this system. My lack of Linux experience is mostly to blame for that. Any ideas?

Thank you for the support

---

