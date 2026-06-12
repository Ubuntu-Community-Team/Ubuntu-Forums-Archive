---
title: "[HOWTO] Make Java work in Firefox"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-07-15
Being new to Ubuntu and linux it was a problem for me to make Java work in Firefox.  I needed it for my internet bank so I had to either make it work or go back to Win XP.

With the support of some of the members of this forum I finally made it work perfectly. **This is how to do it:**


[INDENT]First go to [http://www.getautomatix.com/](http://www.getautomatix.com/) and install Automatix. 

Next open Automatix and locate the tab "Install".

Click "Codecs and plugins". 

Choose "SUN JAVA  1.6 JRE" and click the Start button.[/INDENT]


That's it! Next time you open Firefox Java will work.

---

### Post by Gausian on 2007-07-15
actually the java website has some pretty simple instructions for installing java and compenents.

you can also easily install it from synaptic.

no need for automatrix

---

### Post by pointyblue on 2007-07-15
You are right.

The only problem is they didn't work on my machine. Tried several times and the installation would always stop halfway through and wouldn't finish.

Couldn't access synaptic after that or otherwise install other applications and had to reinstall Ubuntu. (Probably because I'm new at this, I know.)

The method I described above works like a charm and will hopefully spare others of the problems I've had with Java + Firefox.

---

### Post by mcduck on 2007-07-15
Why bother with Automatix when you could just go to Applications - Add/Remove and install "Sun Java 5.0 Plugin" ;)

---

### Post by odiseo77 on 2007-07-15
yep, and don't forget to ***sudo update-alternatives --config java*** after installing sun's java in order to make it the system default java ;)

---

### Post by pointyblue on 2007-07-15
@ mcduck:

?? I can't install java via "Add/remove" on my system - the option is not there.

It can be installed with Synaptic, but it's an old version and even though it seems to install allright it doesn't work when I try to log in to my bank. Installing java via Automatix does.

Btw with Automatix you can install a lot of other cool software as well. It's very easy to use, which is probably what you need after just having switched from Windows.

---

### Post by mcduck on 2007-07-15
> **pointyblue said:**
> @ mcduck:

?? I can't install java via "Add/remove" on my system - the option is not there.

It can be installed with Synaptic, but it's an old version and even though it seems to install allright it doesn't work when I try to log in to my bank. Installing java via Automatix does.

Btw with Automatix you can install a lot of other cool software as well. It's very easy to use, which is probably what you need after just having switched from Windows.

It's there, at least in Feisty, you just have to set the dropdown box in the top right corner to "All Available Applications"..

---

### Post by testube_babies on 2007-07-15
Much better to avoid Automatix (when possible):

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

The Ubuntu Guide has more "official" methods of installing most popular software packages.

To quote from the guide:
"Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu."

---

### Post by kstella on 2007-07-17
Thanks, guys. Was wondering about this.

---

