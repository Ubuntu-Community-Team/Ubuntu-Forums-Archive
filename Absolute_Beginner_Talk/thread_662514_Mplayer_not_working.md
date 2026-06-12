---
title: "Mplayer not working"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-09
Ever since i got xine for totem, my mplayer has stopped working.  How can i get it working again?

---

### Post by RomeReactor on 2008-01-09
Hi. Does Mplayer crash/freeze? try launching it from the terminal to see if it dumps a crash message:
```
gmplayer
```
then use its menu to open a video file.

---

### Post by jordank on 2008-01-09
it works to launch from the console, but it just tells me it cant find the .avi file

---

### Post by RomeReactor on 2008-01-09
As far as I know, Mplayer uses its own set of codecs, so changing Totem from Gstreamer to Xine should make no difference. In the terminal change directory to where the you have video file you want to open. Then write **gmplayer** and begin writing the first word in the name of the file, and press TAB; it should autocomplete the filename.

---

### Post by jordank on 2008-01-09
it used to work fine, until i got xine.  I've just been right clicking files and saying "open with mplayer" and that gives me the error "can not find file"  there is somethin else going on, because i know i have the correct directory. any other suggestions?

---

### Post by shareMenaPeace on 2008-01-09
start synaptic package manager from ADMINISTRATION tab than uninstall mplayer and reinstall? (maybe use complete removal)

---

### Post by RomeReactor on 2008-01-09
The problem might be related to its configuration; try deleting the **.mplayer** folder in your home directory. Close Mplayer and:
```
rm -R ~/.mplayer
```
Then open Mplayer again and try to play the file. Does this happen with other videos?

---

### Post by jordank on 2008-01-09
yeah happens with all videos. i'll go try the synaptic approach right now

---

### Post by jordank on 2008-01-09
uninstalled with synaptic (complete removal) then installed again and the same problem occurs 
"failed find ...."  

Next idea?

---

### Post by jordank on 2008-01-09
The method you suggested, Romereactor, didn't work either :S

---

### Post by k4eez on 2008-01-09
hi mark here
i to am having some issues with a bunch of apps
first of all i am new to Ubuntu 7.10 thats what i have install on a server with 80gb eide drive and LG dvd r/w with light scribe cant find the software for the light scribe either, but thats another problem... cpu running true intel 2.50ghz 2gb raM 3DFX 128MB AGB 8X CARD  with dual a/v out...m board is PT800 CE-A with built in VIA sound and chip set

anyhow, i can run mplayer from the pull down menu's as i have my tool bar at the top of the screen, but it wont play anything, when i try to open it up via command line in the terminal window; well here take a look for your self's sereen dump:

Ubuntu v 7.10
k4eez@RRserver:~$ gmplayer
The program 'gmplayer' is currently not installed.  You can install it by typing:
sudo apt-get install mplayer

You will have to enable component called 'multiverse'
bash: gmplayer: command not found

k4eez@RRserver:~$ sudo apt-get install mplayer

[sudo] password for k4eez: **************
Reading package lists... Done

Building dependency tree       
Reading state information... Done

E: Couldn't find package mplayer
k4eez@RRserver:~$ 

no matter what app i try to install it will return the E: Couldn't find package

WHY?
also how do i enable component called 'multiverse' and where do i get it from?
what will be the syntex to use 
i have tried the following syntax:

k4eez@RRserver:~$ enable multiverse
bash: enable: multiverse: not a shell builtin
k4eez@RRserver:~$ 

so then i tried:

k4eez@RRserver:~$ multiverse
bash: multiverse: command not found
k4eez@RRserver:~$ 


how do i tell it to do this
i also need adobe reader, flash player

one more thing i have noticed, when visiting some web sites at the top of fire fox theres an active x control telling me that i have some components missing EG flash player, i click in the pop up active x, another window from fire fox appears, i click on install flash player and a box appears with a red X saying fire fox needs to be restarted, i click ok fire fox restarts and loads the web page and then it says i have components missing ....
the whole process starts over again....
how do i install flash player, i have down load's it but as i am so use to windows i am looking for a .exe file or install file  what do i need to do once i have down loaded files that are archived.rpm etc etc can some please enplane all the above...

thank you in advance
mark
Clearwater Fl 

  




> **jordank said:**
> Ever since i got xine for totem, my mplayer has stopped working.  How can i get it working again?

---

