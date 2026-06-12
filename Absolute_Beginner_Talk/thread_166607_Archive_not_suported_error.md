---
title: "Archive not suported error"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Soundsofexile on 2006-04-26
I've been trying to install software packeges for my laptop, for instince the PCMCIA-cs and it keeps coming up with an archive not suported error.
This is my first time dealing with Lunix period so I'd really appreciate the help, thank you.
J

---

### Post by dave9191 on 2006-04-26
How are you trying to install them? 

You should be using synatpic (graphical interface) or apt-get (command line interface). Once you have enabled additional repositories ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) you can open a terminal  and type

sudo apt-get install pcmcia-cs

and that will download and install the package for you. You will have to enter YOUR password when promted. 

Hope that helps.

--
Dave

---

