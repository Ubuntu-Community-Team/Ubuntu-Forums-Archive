---
title: "Dead pixel like dots problem after fresh install"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by babacan on 2007-06-22
Hello I am a newbie Ubuntu user,
After a fresh install by using a guide I installed nvidia drivers (I have 6600 gt):

> Install nVidia Driver
sudo aptitude install nvidia-glx

Tell X to use the new driver:
sudo nvidia-xconfig --add-argb-glx-visuals

Disable the nVidia logo startup splash:
sudo gedit /etc/X11/xorg.conf

Add the following line to the "Device" section for your video card:
Option "NoLogo"

Restart X (CTRL + ALT + BACKSPACE). Done!

After that , I tried to change the resolution by:

> Increase Screen Resolution

This is the fastest way to increase your screen resolution to the native display. Ignore the lengthy tutorials on other sites; this is all you have to do. First, backup your X configuration file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If anything goes wrong, simply replace the original xorg.con file.

1.

Edit your xorg.conf so that it includes the proper HorizSync and VertRefresh values in the "Monitor" section. The values can be found in your monitor's manual, or you can search for them online.
sudo gedit /etc/X11/xorg.conf

Mine looks like this:
Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28.0 - 64.0
VertRefresh 43.0 - 60.0
Option "DPMS"
EndSection
2.

Add your resolution to the proper "Display" subsection in the "Screen" section. For instance, if your DefaultDepth is set to 24 (look near the top of the "Screen" section for this), you add your resolution to the subsection with 24 as the Depth value.
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
3.

Save the file, then restart X (CTRL + ALT + BACKSPACE). Done!

Now here is the problem: I time to time see dead pixel like dots that are glowing randomly , especially on pictures and videos.
Any idea how to fix this?

Cheers

---

