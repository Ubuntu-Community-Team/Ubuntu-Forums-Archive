---
title: "anyone have the tutor? for alternatives Ubuntu installation?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by jaya28inside on 2008-02-09
i suggest
some one could post the tutors
here...

meanwhile... you all knew that i'm new here...
that's why need help.

what's should i do next
after completing the frist installation of UBUNTU

via ALTERNATIVE mode?
coz lastly i download from it
the CD is not the Desktop then...


plzzz post post post...need guidance...!! :'(

---

### Post by jan quark on 2008-02-09
the one and only :)


[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

it is a very good guide, with many steps and pictures

also you may ask here whatever you want to know

do you have already installed ubuntu or are you going to ?

---

### Post by taurus on 2008-02-09
Are you sure you installed the desktop version instead of the server version?  

What happens when you run this command from a prompt?

```
startx
```
If you get an error message about command not found, then you need to install Gnome window manager on your system then.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by jaya28inside on 2008-02-09
dont say i need downloding more CDs... from this website...

i'm having probs right now...
coz each time i connect to internet isnot inside of my room
but in the another places...

and please let all of us know
that i 
dont use any Network Card on that my PC

so i just Disabled it from my BIOS...
no need to setting it on my fresh Ubuntu right?

---

### Post by jaya28inside on 2008-02-09
so then i reach that Command 

> 
STARTX


and then appeared the SAFE MODE of looks like 
Windows Safe mode... then ?

i really2 confused
coz in Windows... i need to install the appropriate Driver
to get the Graphical and sound working on...

but here?
i really2 dont know what to do next....

---

### Post by taurus on 2008-02-09
So you are running at a low resolution.  Exit Gnome window manager and at the prompt, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```
What you list the spec of your machine especially the graphic card and monitor?

---

### Post by jaya28inside on 2008-02-09
OMG
something goes wrong here....

i dunno
firstly come
it appeared the error "user switch" or something like that??

i dunno whats that anyway?
and then it said unexpectedly not closed or what.... 
i just come up and then receiving that message?
meanwhile i still new fresh installing on it. . . . :(

---

### Post by jaya28inside on 2008-02-09
> **jan quark said:**
> the one and only :)


[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

it is a very good guide, with many steps and pictures

also you may ask here whatever you want to know

do you have already installed ubuntu or are you going to ?

that links didnt use the CommandLine SYstem
instead 
he just use the normal way....
the Text mode ... first selection... OMG!

but last time i didnt use the "gdm" on the last command... successful...
is it correct or i need to install again the "ubuntu-desktop"?

guidance please for new users.... (sorry friends... i did many questioning)  :popcorn:

---

