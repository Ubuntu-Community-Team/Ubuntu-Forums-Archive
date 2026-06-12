---
title: "newbie internet help"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by draleaf on 2006-12-18
I have installed ubuntu 6.06 and it went great but i cant get on the internet. I have a little home network set up useing linksys WRT54G router with the updated firmware.I have 2 windows boxes on it and they work fine. im not sure what ethernet card in useing as it is an old box that was given to me. What other info can i give that would help in tracking down the problem? keep in mind in so new as not to know how do do much of anything so step by step is going to be needed.I am in awe of the opensource movement and  i have really been wanting to learn all i can about ubuntu.
thank you for any help given.
Doug Greene

---

### Post by lyceum on 2006-12-18
I don't know how much I can help, but to get you started, was the line pluged in to the internet card when you turned the PC on? And I am assuming that it has never worked, right? Also, this is wired, not wireless right?

---

### Post by nephish on 2006-12-18
one of the best helps we can have is knowing your network config.
open a terminal and type ifconfig

copy the output here so we can see. 

are you trying to connect by dhcp (auto ip address) or are you giving a static ip.

all of this will help us out. 

btw, to copy something out of gnome-terminal,  use the file menu, ctrl-C doesn't work.

i am sure you can get up and running online with all of the combined help on this forum.

welcome to Ubuntu and Linux !

---

### Post by gunksta on 2006-12-18
Depending on what your configuration is, ifconfig may not contain everything...afterall, something isn't configured correctly.

Post the output from the command

lspci

to this thread.

--andy

---

