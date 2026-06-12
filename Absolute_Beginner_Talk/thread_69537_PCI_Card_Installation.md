---
title: "PCI Card Installation"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Corrupt on 2005-09-27
Hey,

I think that this is because i dont have the right drives for my new wireless card (Netgear wg311v3), but i also have no idea what is ment to happen, how to install the software for it and/or drivers?

---

### Post by nocturn on 2005-09-27
[QUOTE=Corrupt]Hey,

I think that this is because i dont have the right drives for my new wireless card (Netgear wg311v3), but i also have no idea what is ment to happen, how to install the software for it and/or drivers?[/QUOTE]

I'm afraid it is not natively supported in Linux as far as I can see.
The workarround is to set up ndiswrapper with the Windows driver.

---

### Post by Corrupt on 2005-09-28
alright i have no idea what you just said, mainly with the ndiswrapper with the windows driver, can i get you to please dumb it down

---

### Post by Borusa on 2005-09-28
First, you need the windows drivers for your card. They will either be on the supplied CD or downloadable. If downloadable, download and unpack.

Then follow the instructions in this wiki page - 

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

It's not very hard, just take it slow and come back if you have any more problems!

---

### Post by Corrupt on 2005-12-31
alright, now i tried doing that and it didnt work, i also have no idea how to use synaptic. can you give us a n00bs step through please

i mhave manged to install the ndiswrapper but i am getting this 

bash: sudo ndiswrapper -i /home/corrupt/desktop/WG311v3.INF : command could not be found

ok that problem is now solved but i dont know what is happening here. I do a 

ndiswrapper -m and it says that the file already exists or somthing to that degree
but i do a 
modprobe ndiswrapper and it says that there is no file.

:mad: :mad: :mad: :mad: :mad:

---

