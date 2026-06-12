---
title: "Editing config files"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by sju4sju on 2005-12-20
Hi! :D 

Complete linux virgin here..
I've just downloaded and installed the newest Ubuntu DVD onto my old desktop, and it looks great; perfect for my word processing and surfing needs.

I've been browsing these forums for a 'lil while now trying to find answers to stuff I found quirky, but couldn't really find answers for this:


   As my old monitor is very dark, I used the terminal command xgamma -gamma 2.70 to lighten things up a bit.
However, this does not get saved when I turn off the computer.
Checking Save current setup upon shutting down doesn't work.
Which file should I edit to make it permanent? Also, I've tried editing files like xorg.conf, but it won't let me alter/save it..


   Also, none of my other partitions, or my MP3 drive are visible.. how can I get access to them?
   All drives are FAT32

Please answer in a newbie friendly way - In advance, thanks for your help ;)

---

### Post by kosmic on 2005-12-20
To edit (write/Save) files that are outside your home folder you need to have root autority or use the sudo comand.
 
In a terminal window just do -> sudo gedit /etc/X11/xorg.conf and you can save the file in the end :)
 
 
To use a comand every time ubuntu starts just go to administration -> sessions and there's a little place (I can remember the name) where you can define the aplications you want to start automatic with Ubuntu.
 
 
To mount the drives have a look here -> [http://ubuntuguide.org/#automountfat]("http://ubuntuguide.org/#automountfat")

---

### Post by deNoobius on 2005-12-20
[QUOTE=kosmic]
 
To use a comand every time ubuntu starts just go to administration -> sessions and there's a little place (I can remember the name) where you can define the aplications you want to start automatic with Ubuntu.
 
[/QUOTE]

Are you talking about System => Preferences => Sessions /Startup programs?

---

