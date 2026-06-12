---
title: "Help ubuntu freezes at aplash screen loading bar"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by midnight27 on 2006-10-02
I am having problems with ubuntu! I have had to reinstall 3times now becomes something keeps causing it to freeze on startup. Ok I have a amd64 3000+(socket 754) and a geforce 6800 agp, 1gb ram and 360mb worth hd space on a home built desktop pc. Ok I installed amd64 bit version first time got everything up and running including the nvidia driver. Then found out that certain things don't work like wine, java, flash etc. So then I installed kubuntu got everthing working upraded to
k7 32bit kernel and nvidia driver. I opened up some of the extra repositories and must of installed a conflicting prog and boom it hangs on startup. Reinstalled ... KDE and Gnome install (really cool I love choice!) upgraded to k732bit kernel couldn't find the guide that helped me install the nv driver the first 2 times, so I use a few different techniques mentioned in the forums, problem is none of them worked and I think I messed up the xorg config file or uninstalled the driver by installing the settings from synaptic after doing the terminal stuff (I wanted to be able to change card ettings.
.....Now when I boot in either the K7 or 386 kernel starts from grub, it loads all the drivers then the splah screen comes up and it freezes right there, no bar filling up or anything. I can't get into the gui. I can use the recovery mode to goto the terminal, but alas I come from 15years of dos/windows and linux terminal uses different commands. What can I do to get my system back up from the console? I don't want to have to reinstall as I've spent a lot of time getting all my firefox extensions program etc.. 3 timmes allready annoying!!! What command gets you back to the gui from the console recovery mode? What can I do to fix this? Is it my display driver? Most likely!! Any help would be appreciated! cout<<"ROB";

---

### Post by scrattox on 2006-10-02
To start the GUI from the console, type "startx".

If it fails, look back through the text output which is printed (use Shift+PageUp to scroll up) and see what errors are printed.  One of them might give you the clue we need.
In general, errors in the X server are denoted by (EE) in the output (as opposed to (II) for info messages etc.)

Give it a try and post some results.

And stop ](*,) 

;) ;) :D

---

