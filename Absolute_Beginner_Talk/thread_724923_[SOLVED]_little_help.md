---
title: "[SOLVED] little help?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-15
I'm getting this error in synaptic package manager while trying to install VLC player. I tried fixing but end up stuck in what seems like a sun java licence??

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by uberlube on 2008-03-15
open a terminal and run

```
 dpkg --configure -a
```

This should fix your problem. If it says something like 'permission denied' the type in 

```
 sudo su (and then type in password)
```

Then repeat the first line :)

---

### Post by kleo skywalker on 2008-03-15
Applications-->Accessories-->Terminal. Type ```
sudo dpkg --configure -a
``` It'll ask you for a password, just type yours.

---

### Post by Helios1276 on 2008-03-15
cheers guys! anyone got a fix for windows getting stuck at the top of the screen? as in the top of the window goes off the visible screen everytime i open one??

---

### Post by uberlube on 2008-03-15
Right click on the panel and make it "hide" in the options, then pull your window down and try not to put it there again, lol. This has happened to me a few times :lolflag:

---

### Post by pro003 on 2008-03-15
you were probably experimenting with visual stuff like emerald or something so whatever you did you must reverse it.... I mean "go back", uninstall and try again but follow the instructions carefully.

good luck

---

### Post by Helios1276 on 2008-03-15
ya..i think your right, got over excited with compiz maybe..while im at it ..how do i get emerald? lol

---

### Post by corney91 on 2008-03-15
If any part of the window is visible, you can old alt and drag the window down, clicking on the window anywhere, not just the titlebar.

---

### Post by Helios1276 on 2008-03-15
nahh its not letting me drag anything, i can de clutter till i see the windows but i cant drag em down ( including with alt key pushed?), im guessing i need to reinstall compiz so , anyone tell me the quickest route? terminal im guessing but how?

---

### Post by kleo skywalker on 2008-03-15
> **Helios1276 said:**
> im guessing i need to reinstall compiz so , anyone tell me the quickest route? terminal im guessing but how?

Not necessarily, you could do it in Synaptic.

---

### Post by Helios1276 on 2008-03-15
I had a look but when i search for compiz i get a load of files and none seem enabled?? so im unsure of my next step really

---

### Post by Helios1276 on 2008-03-15
problem solved

---

### Post by kleo skywalker on 2008-03-15
> **Helios1276 said:**
> problem solved

You can mark the thread as solved. On the top right corner above the thread there is a "Thread Tools" button, it has a drop-down menu from where you can select "Mark thread as solved".

---

### Post by pro003 on 2008-03-15
Ok, uninstall compiz 

# sudo apt-get remove compizconfig-settings-manager

and then:

# sudo apt-get update

# sudo apt-get install -f

# sudo apt-get autoclean

and 

# sudo reboot 

...This should solve your problem. By the way chose when you log in new xclient session

good luck

---

