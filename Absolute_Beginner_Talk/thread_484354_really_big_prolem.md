---
title: "really big prolem"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by death_god on 2007-06-25
i'm new with ubuntu and i tried to install beryl in it.
And the problem that i have is that now every time i restart ubuntu i get this message that x server is not working and i tried to reinstall ubuntu again and the i get the same message.

i'm using a compaq presario v2000 with an ATI redeon xpress 200m and also i have a dual boot with windows xp
can someone help to fix this or help reinstalling ubuntu 7.04 without getting the massage again.

---

### Post by bigken on 2007-06-25
at the prompt type sudo dpkg-reconfigure -phigh xserver-xorg select your video driver and use the space to select the desired resolutions

---

### Post by Zzl1xndd on 2007-06-25
> **death_god said:**
> i'm new with ubuntu and i tried to install beryl in it.
And the problem that i have is that now every time i restart ubuntu i get this message that x server is not working and i tried to reinstall ubuntu again and the i get the same message.

i'm using a compaq presario v2000 with an ATI redeon xpress 200m and also i have a dual boot with windows xp
can someone help to fix this or help reinstalling ubuntu 7.04 without getting the massage again.

if its brings you to a terminal after the can't start x message then try using this command "sudo dpkg-reconfigure xserver-xorg" (without the quotes of course) and answer the questions if you dont know an answer pick the default that should get you back up.

---

### Post by bigken on 2007-06-25
select ati as your driver

---

### Post by death_god on 2007-06-25
iv'e done that and nothing

---

### Post by Jobbe123 on 2007-06-25
--OFF TOPIC--

Where can i get beryl??

---

### Post by FleetAdmiral74 on 2007-06-25
please, take a SECOND and GOOGLE IT!!!!

man, lots of people here solve problems by googling or searching anyway. fyi, this was to the person who asked where to get beryl.

seriously, google "ubuntu how to install beryl"!

---

### Post by Zzl1xndd on 2007-06-25
> **Jobbe123 said:**
> --OFF TOPIC--

Where can i get beryl??

  	
FleetAdmiral74 is right But.

there are a number of ways I installed from synaptic but make sure you install the beryl manager and Emerald as well if you do it that way.

---

### Post by FleetAdmiral74 on 2007-06-25
sorry about the yelling...I am stressed.

---

### Post by bigken on 2007-06-25
ok try it again and select vesa as your driver

---

### Post by bigken on 2007-06-25
when you have run the command type startx

---

### Post by Jobbe123 on 2007-06-25
> **FleetAdmiral74 said:**
> sorry about the yelling...I am stressed.

Thats okay..

---

### Post by death_god on 2007-06-25
ok now i'm posting from my ubuntu os it worked, and working, now i'll go and google how to install beryl on my laptop.

[SIZE="7"]thank you guys[/SIZE]

---

### Post by bigken on 2007-06-25
> **Jobbe123 said:**
> --OFF TOPIC--

Where can i get beryl??


sudo aptitude install beryl

sudo aptitude install emerald

---

### Post by FleetAdmiral74 on 2007-06-25
hehe, just know beryl will very likely crash your desktop at least once within a week. guarantee you will be coming back to the forums for help  :)

---

### Post by bigken on 2007-06-25
Im running fusion on my kde desktop very nice [IMG]http://ubuntuforums.org/attachment.php?attachmentid=36464&stc=1&d=1182810393[/IMG]

---

### Post by Jobbe123 on 2007-06-25
fusion looks nice

---

### Post by bigken on 2007-06-25
> **Jobbe123 said:**
> fusion looks nice

check it out[ here;)]("http://www.youtube.com/results?search_query=compiz+fusion&search=")

---

