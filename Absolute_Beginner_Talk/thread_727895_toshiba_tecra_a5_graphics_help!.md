---
title: "toshiba tecra a5 graphics help!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by westyonfire on 2008-03-18
This is probably easy to fix; I just don't know how to do it :( I've got a Toshiba tecra A5 which has worked perfectly since I installed ubuntu on it. The graphics driver was detected somehow and I got all the eye candy going no problem...except the other night I was trying to play a dvd on a big screen plasma through my laptop and fiddled round with the Preferences > Screen & Graphics settings and I  messed something up. I don't remember what the settings were before but I can only run ubuntu in low graphics mode now. Can anyone pleease help? Device manager says the pc has a "Mobile 915GM/GMS/910GML Express Graphics Controller"

any help would be muchos appreciated.

---

### Post by duncan.hawthorne on 2008-03-18
hey, should hopefully be fixeable,
now when you say you went into prefernces> screens and graphics, you should be clear that you went into administration >screens and graphics.....
when you go into the administration section, things can break

the settings  for X (the graphical bit) are stored in a file called xorg.conf in /etc/X11
all you need to do is backup the old (working) file

be careful with what your doing, things can break if you are careless.

so run 
sudo nautilus 
in terminal. this opens the filebrowser with superuser permissions so you can edit important system files.
browse to the folder /etc/X11 and you shoudl see files called xorg.conf and xorg.conf.something....

make a copy of your current xorg.conf, and all the other xorg.conf.something files just in case

 then rename one of the other xorg.conf.something to xorg.conf . your computer will then look at this file. look at the date modified of the files if you have several to choose from to choose a file after which X worked properly (eg the one created when you first installed ubuntu is a good bet). log out, log in, should work :)

post back for any further problems

---

### Post by westyonfire on 2008-03-18
hi, thanks for the reply.
I'm in the X11 folder and theres...xorg.conf then there xorg.conf.1 through to xorg.conf.13. theres also xorg.conf.failsafe through to xorg.conf.failsafe.8. The thing is _none_ of them have a modyfied date before the date I fiddled around with the Screens & graphics settings...

---

### Post by westyonfire on 2008-03-18
Hi again,
I went ahead and renamed the file which was modyfied at the earliest date...(which is still after the time I fiddled around with the settings) to xorg.conf. I logged out, then in and still the same. It wont let me turn desktop effects on...any other ideas? I'm really hoping I dont have to do a reinstall...

---

### Post by duncan.hawthorne on 2008-03-19
you might want 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo apt-get install --reinstall xserver-xorg-video-intel

or try fiddling with the screens and graphics thing, choosing you correct driver (did you change the driver? or just the resolution?)

if you are in low resolution (are you?), you could probably just edit the xorg file resolution section (always keep a backup of the xorg.conf file).

what output in the terminal do you get when you run 
compiz

---

