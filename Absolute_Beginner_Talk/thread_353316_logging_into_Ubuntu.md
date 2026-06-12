---
title: "logging into Ubuntu"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by philmiller on 2007-02-04
I have installed Ubuntu successfully after much noob apprehension and it has been working fine.  Until this morning when I booted it up and I entered my username and password it looked like it was accepted but then the screen went black for a few seconds then it showed the login screen again.  First of all if I can set it up so I do not have to log in that would be great.  I am the only one in my house who has even heard of Linux and the boot loader is defaulted to load XP so I can limit confusion for my wife.

I have never changed the password or username.  If I enter an incorrect username or password it responds differently, it will tell me I have entered an incorrect username or password.

So my question is how can I log in if it won't get me past the login screen.  Is there some sort of "safe" log in? 

also how do i get it to not ask me to log in every time I boot up Ubuntu.

As always thanks ahead of time for the help, you guys rule!

Phil

---

### Post by shareMenaPeace on 2007-02-04
When you see the login screen choose

session -> failsafe 

try if it works this way.

---

### Post by annda on 2007-02-04
your xserver seems to fail. did you change anything in the display/graphics department before it stopped working?

---

### Post by philmiller on 2007-02-04
The only thing i changed was the default setting in the bootloader.

---

### Post by philmiller on 2007-02-04
I think i have an idea of what might have happened.  I think i filled up my /root partition.  When i tried to log in in a failsafe session it told me that there was not enough room to write something.   And the last time i was using ubuntu I did install a bunch of packages and ran out of room.  That is exactly what i was going to try and do when  i logged back in was delete some of the unnecessary packages I installed just to see what they were or if they were worth it.  

So now i need to figure out how to increase the /root partition.  Whould i be able to do it from a gparted live cd?  Will this mess up any other partions? do I need to delete and then recreate a partiton?

---

### Post by shareMenaPeace on 2007-02-04
If you could make a little room (see your /home/ folder) you can install gparted

System -> Administration -> Synaptic Package Manager 

search gparted and check/apply to install.

---

### Post by philmiller on 2007-02-04
> **shareMenaPeace said:**
> If you could make a little room (see your /home/ folder) you can install gparted

System -> Administration -> Synaptic Package Manager 

search gparted and check/apply to install.
I would if i could even get logged in.  I can't get past the login screen

---

### Post by shareMenaPeace on 2007-02-04
Use the live cd gparted than. 
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

