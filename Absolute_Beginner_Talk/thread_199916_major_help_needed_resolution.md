---
title: "major help needed resolution"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by mrgreaper on 2006-06-19
ok when i was installing i couldnt read any of it as the resulotion was smaller then the pannels (640x480) 
i just figured this was because of the live cd 
but now i have booted up i still cant change the resulotion my monitier can handle 800x 600 ! but the option aint there only 640x480 at 60hz can be selected

---

### Post by cacharreo on 2006-06-19
Start in console mode and use:
***sudo dpkg-reconfigure xserver-xorg***
Be sure that in the monitor configuration part you mark the desire resolution modes

---

### Post by MaximB on 2006-06-19
or if it doesn't work - install your graphic card
you can look for dozens of topics in this forum for help

---

### Post by mrgreaper on 2006-06-19
the gcard is a built in afair no idea what it is
no idea how to start it in console mode
this may be a mute point though
because

it killed my windows partition
i cannot vnc into it
i had no choice of applications to install during the install stage so that means i have to find apache and python and mysql etc etc etc etc
it cant see ANY of my network shares even though the ethernet card aperantly is active and it does access the inter net
and all this from a linux that claims to be user friendly!

all in all is taken me 7 hours to back up my data and install this (i didnt backup the windows stuff i thought that would ramain untouched)
i`m gonna explore it a bit but im thinking i may just go back to suse 10 

i have to say my advice (personal only) avoid ubuntu

---

