---
title: "KDE doesn't start up"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by CrazyArcher on 2008-02-16
Hello

I use Kubuntu 7.10. For some reason, teh desktop wouldn't start when Kubuntu loads, I only get the console screen. I can log in and perform operations from it, but the desktop just wouldn't load. 
Ideas?

---

### Post by smartboyathome on 2008-02-16
Try running startx after you login from the console. Does KDE start up? If not, are there any errors when X crashes?

---

### Post by mac9416 on 2008-02-16
That happened to me with Gnome. I reformatted and reinstalled. Yuck. I would like to know if there is a way to reinstall Gnome/KDE without losing personel files/settings. I am assuming that's what you want too?
Good luck.:)

---

### Post by CrazyArcher on 2008-02-16
Thank you for fast responce :)

Tried 'startx'. I got it starting up, displaying all kinds of regular info (version etc...) and then I got this message:
Fatal server error: no screens found
XIO: fatal IO error 104 (Connectioin reset by peer) on xserver ":0.0"

What can be the matter here? :confused:

---

### Post by mac9416 on 2008-02-16
I just joined up in this forum, but I am busy killin' time so I Googled for you and found this:
[http://www.debianhelp.org/node/1190]("http://www.debianhelp.org/node/1190")
The first posts looked rather depressing, but the VERY last one says that someone fixed it.
I hope this helps!:)

---

### Post by CrazyArcher on 2008-02-16
How do I upgrade xserver from the console? :???:
That thread is focused around hardware, but my graphic adapter is a lame VIA onboard graphic chip, nothing exotic. That's odd...

---

### Post by mac9416 on 2008-02-16
Yikes! Just remember I'm a noob too.:)
I believe you go to Applications>Accessories>Konsole (at least I think its Konsole) and type at the prompt something like "sudo apt-get update xserver". Now, DON'T RUN THAT COMMAND! I just think that the command may go something to the tune of that, not necessarilly to the letter. I Googled it and didn't find the exact command, but maybe a moderator knows it.
I hope I've been more of a help than a hindrance. :)

---

### Post by Crafty Kisses on 2008-02-16
> **CrazyArcher said:**
> Hello

I use Kubuntu 7.10. For some reason, teh desktop wouldn't start when Kubuntu loads, I only get the console screen. I can log in and perform operations from it, but the desktop just wouldn't load. 
Ideas?

Can you boot into verbose mode?

---

### Post by CrazyArcher on 2008-02-16
Yep, I can. Tried that, everything seems to go okay, and when it's KDE's turn to load, it just stops and asks for login.

---

### Post by CrazyArcher on 2008-02-17
Update: I restored xorg.conf from a backup copy, and tried startx again. I got an X as a mouse cursor and some kind of gray background. That's it.
I looked at the log, and saw there plenty of lines saying  
"VIA(0): not using default more "X*Y" (bad clock/interlace/doublescan)" for any video mode. VIA is my mighty onboard graphic chip. 
Are video drivers broken or something?

---

