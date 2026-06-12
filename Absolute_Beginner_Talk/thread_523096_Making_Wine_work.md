---
title: "Making Wine work"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by DarchAengel on 2007-08-11
I just installed Wine and am trying to install a game off of a CD.  I have the configuration screen up but not sure what to do beyond that.  No matter what I do it won't recognize the setup file.

---

### Post by zero244 on 2007-08-11
Ive tried wine as well and it is not easy to use. For one thing the fonts are too small to see when you run a program inside it.
I suppose if you turn down the resolution on your monitor while using Wine would fix that.
Your going to have to do some research and read some how tos to get it working.
To be honest I dont know why it isnt easier to use.

It does work for many Windows programs including some games.

Keep us posted on your success.

---

### Post by kronk on 2007-08-11
CD is mounted dude ?

If so just change directory to your cdrom then type "wine setup.exe" if setup.exe is the install file :)

EDIT: Oh what's the game ?

---

### Post by Acglaphotis on 2007-08-11
Which game? Have you seen it on the appdb?

---

### Post by DarchAengel on 2007-08-11
It is Diner Dash and there is nothing on the App db about it...
I got it to install but I am getting some weird stuff on my terminal.  You can see it on [http://paste.ubuntu-nl.org/33374](http://paste.ubuntu-nl.org/33374) I try to click on the button to start it and nothing happens.  Someone mentioned something about gecko but I can't find it.

---

### Post by splintercellguy on 2007-08-11
What version of Wine are you running?

---

### Post by DarchAengel on 2007-08-11
0.9.43

---

### Post by Jofaba on 2007-08-12
This is my first time ever using Wine and I can't say this works, but I'm trying to install Half Life 2 right now and out of pure chance here is what I did to get the install process to at least properly start:

Open up the CD drive as if it's a folder. Find the install file and right click on it. Choose "open with" and under custom comand simply type in 

wine

That actually got the install process working. I may destroy something this way but just thought I'd share what's working so far for me. I'll let you know if this actually gets a playable game on my pc.

UPDATE: When the install process asks for the second disc, I couldn't get it to eject. I got a pin and force an eject (you know that emergency hole in the front of the cd drive?). After putting the new disk in, it took a second but the new cd mounted and the "ignore" turned back into a "retry" and the install is continuing.

K, guess I need to find the "right" way of doing it. On disk three the installation stopped in error. =(

---

### Post by buntunub on 2007-08-12
to eject cd's during wine installs, in terminal type wine eject.

---

