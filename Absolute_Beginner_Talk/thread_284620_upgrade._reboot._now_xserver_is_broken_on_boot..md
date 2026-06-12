---
title: "upgrade. reboot. now xserver is broken on boot."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by justinol on 2006-10-25
hi. i am true newbie. especially when i get a screen coming up on booting that says xserver has a probelem (or is courrupt or couldn't be init or something like that) and somehting called GDM won't or cant be loaded. 

so i push ok twice and am suddenly faced with a text input asking for my login.

text? only? where is the graphical sexiness that ubuntu is? no mouse cursor? it's like 1983, but worse because i know the alternative. and i don't know what to do.

could someone please tell me how to fix this. 

sequence of events leading up to this are. Ubuntu asked me to update (i am using edgy cause i prefer its feel to dapper). so i do a sudo-apt etc etc to install. the i think... hey let me try out enlightenment becuase it looks good. so i install enliughtenment using synaptic. then I log out and try logging in on enlightnement 0.16 under gnome which is a log in option i get. i can get in but an error message comes up (if i recall correctly it was something about GDM again) so i reckon that its screwy becuase i am using the latest nvidia driver (which replaces metacity or whatever window manager) and so the update maybe needs a reboot.

so i reboot.

only to get a xserver error message (complete with unsexy green and yellow and white type) and then ultimatley get stuck on a text only screen. i type my username and password and log in successfully. but now what? all i see is black screen with white type.


help most appreciated. 

oh, and please remember i am new so please show it in all steps and as it should be typed. although how the hell am i going to see the instructions on a text only screen (guess i'll have to see them using wondows, print them out and then follow them on linux, whcih sorta defeats the point of using linux entriely doesn't it?)

as a suggestion i recommend that Linux or Ubunt develop a text only commnad like 'Emergency' that gives 4 options (for example 1) restore point for linux, 2)safe mode, 3)last working mode, 4) just get it working) that can save most borked systems. that is something that would make linux much more user friendly to newcomers like me.

cheers.

---

### Post by Josey on 2006-10-25
I'm not sure what happened exactly but providing as much info as possible like what was upgraded would help.

I would persally try to install another ubuntu desktop like xubuntu just to get myself back to a gui and try to fix gdm from there.

> sudo aptitude install xubuntu-desktop

after you run that command you can load xfce gui by typing 

> startx

hope that helps

---

### Post by adwait on 2006-10-25
Well, try logging in and using
```
sudo dpkg-reconfigure xserver-xorg
```

Maybe that could solve the problems...

---

### Post by JayTee on 2006-10-25
When you downloaded Enlightenment you changed your Xserver configuration. Enlightenment is an alternative to Gnome in Ubuntu Edgy or KDE in Kubuntu Edgy. You could look in /etc/X11/ for a backup of xorg.conf like xorg.conf~ or xorg.conf.old and copy it to xorg.conf to see if that restores your Gnome desktop. I always make a backup of xorg.conf before I mess with anything that might break the xserver or GDM. You could also try the more involved solution of running sudo apt-get remove "name of enlightenment package" and then run sudo apt-get install gnome-desktop and then run sudo dpkg-reconfigure xserver-xorg. Then type GDM start and see if that works. hth

---

