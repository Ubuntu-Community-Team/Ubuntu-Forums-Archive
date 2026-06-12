---
title: "anyone with fluxbox please help"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-22
Hey,

I Have fluxbox installed and im trying to edit my menu, i know i can go to the ~/.fluxbox/menu file and edit it there... but thats not what i want... i want the file that controls the menu display. i also want to know how to make something start upon login to fluxbox. 

I want to start off there and work my way thru the desktop and edit it to work the way i would like it.. any help is appreciated.

Thanks
~Lance

---

### Post by Kyral on 2005-12-22
I helped write a guide in the Wiki for Fluxbox

[http://wiki.ubuntu.com/Fluxbox]("http://wiki.ubuntu.com/Fluxbox")

Anymore questions feel free to IM me

---

### Post by noob_Lance on 2005-12-22
i would IM you... but i only have MSN .. and you have AIM.. but as for your wiki... well it didnt help lol... i want the menu file that will parse the menu file :p not the menu file itself that is the easy part.

~Lance

---

### Post by Kyral on 2005-12-22
The menu file that will parse the menufile.....what? You mean the thing that displays.....uhhhh......could you give a practical example of what you are trying to do, because I have NO idea right now

---

### Post by noob_Lance on 2005-12-22
hahah sorry i know i am very confusing.. i got my wisdom teeth out earlier this week and those T3's are still messin me up.. but anyways,,,want i want is the file that handles the menu operations. that will take the text file and make it into a fully working menu that you see when you right click.

~Lance

---

### Post by Kyral on 2005-12-23
...I think that the Fluxbox binary does that itself...

---

### Post by noob_Lance on 2005-12-23
hm.... ok.. well i guess ill have to rework that idea lol... but anyways... about the load on startup.. my friend tried to help me... but since i dont start fluxbox from the command line, i dont have a ~/.fluxbox/startup file... 

any ideas now??

Thanks
~Lance

---

### Post by r0ll3r on 2006-01-02
hi there,
on this page [https://wiki.ubuntu.com/Fluxbox]("https://wiki.ubuntu.com/Fluxbox"), they say you have to do the following. In a terminal, execute
```
$ sudo nano /usr/share/xsessions/fluxbox.desktop
```
When you see the following text:
```
exec=fluxbox
```
replace that line with
```
exec=startfluxbox
```
Once you have finished editing /usr/share/xsessions/fluxbox.desktop , restart the X server and log into fluxbox. This way, ~/.fluxbox/startup configuration file will be automatically generated the first time Fluxbox runs.

---

### Post by noob_Lance on 2006-01-02
sweet.. that worked.. thanks alot :D

---

### Post by happogiri on 2006-01-14
Kyral, thank you for the great wiki/tutorial!

---

