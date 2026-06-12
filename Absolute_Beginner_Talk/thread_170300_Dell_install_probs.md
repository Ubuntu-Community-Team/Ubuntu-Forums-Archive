---
title: "Dell install probs"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Carbonbasedmistake on 2006-05-04
Hey all,
I have been trying to get ubuntu installed on a dell desktop 733 P3 with a 15 gig hard drive and 256 meg ram. 
My first attempts (8 or so) failed at different locations in the install routine. I finally received a command line and ran:
dpkg --configure -a 
 and had all but the character map library (libcharmap4) (sp) and another broken library?.
I then ran:
apt-get install ubuntu-desktop
 and then had a desktop - next I ran Synaptic Package Manager and fixed the two broken packages. Re ran dpkg --configure -a and had errors. The desktop was cool but unstable. Applications quiting - jumping back to login screen etc. I couldnt install any packages due to the dpkg errors ( ../../src/...  <4 tries) 


I next tried to reinstall using the various boot arguments and tried to just install the server and the server with various boot arguments and its stopping the install all over the place.  Sometimes it stops at the beginning where the keyboard language is entered - sometimes at the partitioner - normally it just hangs somewhere where it is installing base packages. 

I have verified the CDrom and have used two different CDrom drives. 

There is no network connected - I'll be using an external modem - 

Just wondering if anyone else experienced problems with Dell installs and how they got around it. I've been using Linux since 99 - Debian for about a year till smoke poured out of the back of my clone's power supply taking out the motherboard and harddrive. 

Thanks in advance

bob

---

### Post by nanotube on 2006-05-04
since the errors occur at random places rather than one consistent place... i am tempted to suspect bad ram. have you checked your memory recently?

---

### Post by Carbonbasedmistake on 2006-05-04
No I haven't. One stick came from the PC that smoked so I'll pull it and give it a try later tonite. 


Thanks for the input

bob

---

### Post by nanotube on 2006-05-04
[QUOTE=Carbonbasedmistake]No I haven't. One stick came from the PC that smoked so I'll pull it and give it a try later tonite. 


Thanks for the input

bob[/QUOTE]
hehe, smoked ram eh. new, coming to a deli near you. :)

---

### Post by Mustard on 2006-05-04
From the Grub menu at startup, you can choose the 'Memtest' option which will run some tests on your RAM.  The tests are quite time consuming btw.  If it comes up with any errors then you know you have some type of RAM problem.

---

### Post by Carbonbasedmistake on 2006-05-04
It was smoked ram - from the deli of my own making.
I pulled the one stick - reinstalled without a flaw. Beautiful stuff this ubuntu. It found my IAudio ogg player and it was a breeze (sorry) to config the external modem. 
Thanks nanotube and all.


bob

---

### Post by nanotube on 2006-05-05
glad it worked. have fun. :)

---

