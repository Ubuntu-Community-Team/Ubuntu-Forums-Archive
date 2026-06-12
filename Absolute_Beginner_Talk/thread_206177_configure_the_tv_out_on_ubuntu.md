---
title: "configure the tv out on ubuntu"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-29
HI GUYS

I want to watch films and pictures on my laptop onto the TV.
Have connected the laptop with a video cable to the video out on my laptop to the TV. 
How do I go from here??

thanks

sam

---

### Post by unf on 2006-06-29
[QUOTE=wannabesurfer]HI GUYS

I wan to watch films and pictures on my laptop on the tv, I have video out, and connect it to the TV, how do I go from here.

thanks

sam[/QUOTE]

:lol: 


Well.. this means I have to gues that what laptop you have. #-o

---

### Post by wannabesurfer on 2006-06-29
hey 
well the name of my laptop is IPC, pentium III, driver of my graphic card is silicon motion lynx3DM,

---

### Post by unf on 2006-06-29
What driver are you using? 

type:
cat /etc/X11/xorg.conf | grep Driver
to terminal so we can se what driver is you graphic card is using.
You can try adapt some guides that are in the forum.

---

### Post by wannabesurfer on 2006-06-30
Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "siliconmotion"

---

### Post by wannabesurfer on 2006-06-30
I am wondering where in ubuntu desktop menu can I organice so I can watch pictures, video etc on TV or projector. 
In windows, choose settings, display and configure secondary screen to be primary. 

how to do it in ubuntu??

---

### Post by cowley on 2006-06-30
hi, assuming your graphics card sends out to tv you will have to edit the xorg.conf file. its easy enough and there is plenty of info about it within the forums.

sudo gedit /X11/xorg.conf

simon

---

### Post by raptros-v76 on 2006-06-30
if you used an nvidia card, i could help you no problem. but, iven ever heard of siliconmotion cards. im sure theres something around that will tell you how. if you do a websearch, mace sure to put in the phrase "xorg.conf".

---

