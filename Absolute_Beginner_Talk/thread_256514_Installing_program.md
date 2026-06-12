---
title: "Installing program?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-13
Ive setup lm sensors sucessfully on my system and im trying to configure "sensord" daemon with it. 

I found the instructions to install lm_sensors from 
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Ive downloaded sensord file sensord_2.9.1-4ubuntu3_i386.deb onto my desktop but cant find any method of installing it. Can anyone help me?

P.S I need to do it from the command line cos synpatic manager doesnt work!

---

### Post by smelly_sox on 2006-09-13
In terminal *cd* to /home/user/desktop
*dpkg -i sensord_2.9.1-4ubuntu3_i386.deb*

Regards

---

### Post by xyz on 2006-09-13
I don't know the reasons that surround your Synaptic mess, so, in Google, just type: "fix synaptic" and see if one or another link there relates to your particular situation. You should try to fix it.
Good luck.

---

### Post by smelly_sox on 2006-09-13
Yeh, I hadn't noticed that both lm-sensors & sensord are both in the ubuntu pacakges database. The installation method he has chosen uses the make command, so it seems this has been compiled from source. That's probably the reason synaptic isn't playing nice, it doesn't realise lm-sensors is installed.

---

### Post by meniscus on 2006-09-13
So what do you advise? That command you gave me earlier returned an error when i was loogged on as myself(required superuser priviliges)then when i logged in as root it gave me another error! Have i messed the system up?

---

### Post by xyz on 2006-09-13
I hope the following link relates to your problem. Won't hurt to try:
> Re: Fix for Synaptic problems after libvte updates
[http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238)
Let us know.

---

### Post by meniscus on 2006-09-14
It worked!! havent a clue what i just did but its fixed!Thanks very much

---

