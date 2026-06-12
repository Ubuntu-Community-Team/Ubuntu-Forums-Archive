---
title: "Installing xorg"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by fragility14 on 2007-07-07
I have been unable to make xorg.conf work in any fashion. It says "Bash: Xorg: Command not found"

sudo apt-get xorg comes back with "invalid operation xorg"


No matter how many times people suggest I use xorg.conf to fix various problems I simply cant access it.

---

### Post by zanazzi on 2007-07-07
xorg is just a file that the x server uses

to use the xorg.conf file to fix things u normally have to open it and edit it.

What problems do u have that u need to edit xorg?

---

### Post by Martje_001 on 2007-07-07
What's the output of 'cat /etc/X11/xorg.conf'?

---

### Post by fragility14 on 2007-07-07
well I've had a variety of sound and other problems, and people have repeatedly suggested i put in xorg.conf and then I am unable to do that and get anything, and no one ever helps me with problems.
 
Specificall right now my sound is crackling when system resources are in use, and web browsers in general work horribly (specifically by darkening and becoming unresponsive.

doesn't xorg autoconfigure settings for you?

---

### Post by fragility14 on 2007-07-07
> **Martje_001 said:**
> What's the output of 'cat /etc/X11/xorg.conf'?

no such file or directory

---

### Post by Martje_001 on 2007-07-07
xorg.conf has nothing to do with sound!! Maby you should put down the volume in ubuntu and just do your sound louder hardware-matic ;)

pfff... many language problems in this post.. sorry ;)

---

### Post by zanazzi on 2007-07-07
xorg holds the configurations.

by editting it u can obviously change them and hopefully get things working.

but before editting it u should creat a back up, so at least if screw things up worse than they seem to be then u can get back to ur current state.

just try opening the file and have a look through it, it might give u more of an understanding of what it does. its located in :   /etc/X11

---

### Post by AlexenderReez on 2007-07-07
but if you really need to configure it...

sudo gedit /etc/X11/xorg.conf

---

### Post by zanazzi on 2007-07-07
> **reez0105 said:**
> but if you really need to configure it...

sudo gedit /etc/X11/xorg.conf


lol wasn't going to tell him/her that yet incase he/she deleted the whole thing, but hey done now :D

or u can type (from the terminal) sudo nano xorg.conf (providing u have told the pc where to look using the cd command)

---

