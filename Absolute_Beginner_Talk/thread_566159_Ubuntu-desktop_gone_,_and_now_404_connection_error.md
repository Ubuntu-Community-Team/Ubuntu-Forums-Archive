---
title: "Ubuntu-desktop gone , and now 404 connection error coming"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by D0PA on 2007-10-03
Hi 

I was trying to do make my soundcard work and i followed this guide 

Getting AlSA driver from fresh kernel 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

i don't know what happened to ALSA drivers 
but it removed my Ubuntu-Desktop 

and now when i restart , it opens up just a terminal 

i tried following 

sudo apt-get install gdm ubuntu-desktop
sudo aptitude update 

even every combination i tried with apt-get and update 


everytime it gives some connection error ...... cannot read from archives or cannot connect ......etc etc 


Please help ... what should i do ??

i have Live installation CD ... can it be repaired with that 


I'm new to linux and and only 4 days to ubuntu 

This error is seriously killing me more then anything .......... :(

---

### Post by D0PA on 2007-10-03
:(

---

### Post by natman on 2007-10-03
Sounds like something wrong with X, when you boot up do you have a list of old kernels to chose from, if so try and older one and see if it works.
Else when you boot up to the terminal, is it possible to undo what ever you did in the frist place?

---

### Post by D0PA on 2007-10-03
That's the problem how can i undid that
what i dis was just removed alsa drivers and again installed them 
on removing ALSA it removed ubuntu-desktop ..... 
and i only had one kernel , it boots in the kernal , i tried to even reconfigure xserver , but didn't worked 

and sorry it's not 404 error 

it's 
111 connection Refused error 
[could not connect to in.archives.ubuntu.org ][192........]

also 
when i tried to ping 

ping -c 5 in.archives.ubuntu.org

all 5 packets were lost .... :(

---

### Post by Terl on 2007-10-03
Sounds like you lost your network connection.  How do you connect to the internet?

---

### Post by D0PA on 2007-10-03
through a proxy server 


ping is sucessful for computers of local network ......

an the internet is working , it's sore prob in my comp ...

---

