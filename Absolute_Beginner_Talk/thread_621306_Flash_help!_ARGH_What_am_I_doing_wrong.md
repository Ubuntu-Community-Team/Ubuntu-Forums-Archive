---
title: "Flash help! ARGH What am I doing wrong?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by DMBrazil on 2007-11-23
frist day on ubuntu

trying to get youtube up and running to maybe get some how-to videos for ubuntu. First thing though i need to get the flash plug-in. So I get the plug in from the link in a .rpm file. After reading the forum i discoverd I needed the alien package.. got that thru synaptic (WOOHOO first download), 

extracted the rpm file onto the desktop

and in terminal : sudo alien i- flash.blah,blah.etc.rpm

terminal did a bunch of stuff then gave me a new comand line. 

that should be it but its still not working... no youtube no flash no nothing.

does it ever get easier??

---

### Post by DMBrazil on 2007-11-23
not to mention i also downloaded compiz to try it out.... i got everything download but havent the slightest idea what to do next! all the forums talk about a perference menu that has a compiz conf setting (WHERE!!!?!?!?!?!?!?). I really really like the potention of ubuntu and hated xp but man... this is crazy...

HELP

---

### Post by Kingsley on 2007-11-23
All you had to do was open up Synaptic Package Manager and search for flash. I think "flashplugin-nonfree" is the exact thing you want.

---

### Post by reesy on 2007-11-23
Try going into the synaptic package manager and search for flashplugin-nonfree and install that it should work fine then

---

### Post by Pumalite on 2007-11-23
Get the new Firefox. It comes with all the plugins and more.

---

### Post by dips_xe on 2007-11-23
whoah, you don't need to resort to alien to get flash running.

just do this:

sudo apt-get install flashplugin-nonfree

and it should be working. i'd also remove that alien package you just installed.

---

### Post by DMBrazil on 2007-11-23
YES! YES! YES! YES! (with a tiger woods fist pump on each!)

VICTORY!!!!! youtube is up and running bettter than everrrr before! 

THANK YOU TO ALL!!!!!

---

### Post by kleo skywalker on 2007-11-24
Next time you need plug-ins, or anything else for that matter, try synaptic first!
Good luck.

---

