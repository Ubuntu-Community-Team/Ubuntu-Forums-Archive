---
title: "mouse help"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-24
well i dont really know whats its called but its a stick int the middle of the g,h,b keys(trackpoint?) 

its causing me problems cause once in a while it goes haywire and starts clicking everywhere(mostly goes in the top right corner)

i have an IBM thinkpad btw

---

### Post by Catewilliams on 2006-08-24
> **L_o_N_e_R said:**
> well i dont really know whats its called but its a stick int the middle of the g,h,b keys(trackpoint?) 

its causing me problems cause once in a while it goes haywire and starts clicking everywhere(mostly goes in the top right corner)

i have an IBM thinkpad btw


I have the exact same problem!
Normally, I just turn off my laptop and it's all better, but I have had to change the mouse settings. System > Prefrences > Mouse.

---

### Post by L_o_N_e_R on 2006-08-24
what do you change?

---

### Post by Rye on 2006-08-24
Hi everyone, 

Would just like to ask, if we are in the beginners community, who’s going to help us?:D 

On a lighter side, I re-installed Ubuntu many times, every time I use it, the mouse does not work. I tried loading the mouse driver from CD but .exe file is not read, although other .txt files are read on the same CD. 

I also noticed that during boot sequence , I get a fatal error when hotplug subsystem loads. Pciehp.ko and shpchp.ko are not permitted. 

Any ideas on how to resolve this? I am new user for Ubuntu Linux and would really like to use the system

---

### Post by L_o_N_e_R on 2006-08-24
hey your filipeno?(sp...)
same here :)

usually mouses are plug in play 

the mouses i have(besides the one built in my laptop) works by just plugging them in

what type if use mouse do you have?

---

### Post by L_o_N_e_R on 2006-08-24
bump is there any way to fix this?

---

### Post by jimrz on 2006-08-24
> **L_o_N_e_R said:**
> hey your filipeno?(sp...)
same here :)

usually mouses are plug in play 

the mouses i have(besides the one built in my laptop) works by just plugging them in

what type if use mouse do you have?

For your trackpoint, have a look at your /etc/X11/xorg.conf file

here is the appropriate section from my T42 that has it working perfectly:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

if you need to edit this be sure to make a backup of your current one from terminal FIRST 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
then
```
sudo gedit /etc/X11/xorg.conf
```

to make changes

---

### Post by L_o_N_e_R on 2006-08-24
do i check it using the second command?

---

### Post by jimrz on 2006-08-24
> **L_o_N_e_R said:**
> do i check it using the second command?

the 1st command will make a backup of your current file, always a good idea in case something goes awry you can revert to the old one.

then the second will open in gedit (or you can use another editor, if you prefer) and allow you to make changes. Once open scroll down to the appropriate section and compare with the one posted in my 1st reply. after making changes (if needed) save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

---

### Post by L_o_N_e_R on 2006-08-24
its the same and i stll have the problems

---

### Post by jimrz on 2006-08-26
> **L_o_N_e_R said:**
> its the same and i stll have the problems

What model ThinkPad do you have? Try searching these forums to see what others have experiened with same model (I just enter "T42" in the search field for mine). You might also check out the [[COLOR="Sienna"]**_ThinkWiki_**[/COLOR]]("http://www.thinkwiki.org/wiki/ThinkWiki") site, which has tons of useful info for ThinkPad users.

---

### Post by L_o_N_e_R on 2006-08-27
...sorry for the noob question but how can i tell what ver i have?(winsdows is not working)

---

### Post by jimrz on 2006-08-27
> **L_o_N_e_R said:**
> ...sorry for the noob question but how can i tell what ver i have?(winsdows is not working)

when you open the lid it will be imprinted somewhere on it, on mine it is just below the lcd screen towards the lower left corner. if you don't find it or it has worn away, look on the bottom of the machine for serial# or Type: xxxx ( a 4 digit numer). you can search either of these on the IBM support site and learn your model # that way

---

