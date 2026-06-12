---
title: "Display Setting for 2 monitors"
date: 2009-11-07
forum: Apple Hardware Users
---

### Post by fatum on 2009-11-07
I have a Mac Pro Dual Quad that I am running OS X 10.6, Windows XP Professional, and Ubuntu 9.10 on. Connected to this desktop is my 22" Samsung 1440x900 and my 42" Sony XBR6 1080P. So a couple of questions if I may. 

The Ubuntu system seems to treat these two displays as one big one. My wallpaper stretches out and I open up windows and they show up on the TV (which is not pointed at my desk) when I need them on the monitor in front of me. Is there an option to make the 22" monitor my default like I have it set in OS X? 

For movies playing through VLC in OS X and Windows there is an option to play it full screen on the monitor of my choice. Is there an option for this in Ubuntu? I start playing a movie in OS X and in the video menu there is an option for which monitor to play on full screen. There is not an option like this with Ubuntu. 

I believe that my problems all stem from the Ubuntu System itself treating the two monitors as one. Is there a way to change this behaviour? Thank you in advance for any help or guidance that you give me.

---

### Post by fatum on 2009-12-20
Within the ATI Catalyst there are settings for how I wanted my monitors setup. So that is fixed now. You need to run ATI Catalyst from terminal using sudo with

sudo amdcccle

with that the ATI Catalyst opens with root access and the changes are then able to be made. Without using sudo I did not have the privileges to make the changes that were needed.

---

