---
title: "[SOLVED] mo monitor displays a blurry picture"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-12-07
i have a  nvidia card and a amw 19" crt monitor about 3 years old now the card is the onboard video

lspci | grep VGA      gives the following 

> lolo@lolo:~$ lspci | grep VGA
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
lolo@lolo:~$ 


                                 

i am having trouble with the sharpness of the screen i have fiddled with the settings n the monitor,degaussed it ad the connector is screwed in tightly also 

what is happening is a shadow to the right of whatever image or text is on the screen.
if i do a screen shot and flip the image over the shadows stay to the right 

the typing in this page are the worst and reading anything on a website is aggravating it seems to be about 3-4 shadows of a letter are duplicated  with each one less and less till they disappear  

pictures of the screen show it too but if i zoom in on them it is nowhere near as visible 

sometimes this comes and goes but it seems to be getting worse 
i have a kvm switch and a windows machine hooked up to it and it does not happen on that machine 

i dont notice it with a video but if there is a high contrast picture is shows up there

im not sure what to do i have an ati pciexpress card but read that they are a pain to deal with  so i am waiting to see what comes of this before i swap the card out 

anyone have this problem before 

oh if i view that screenshot on the windows machine by way of emailing it to myself it is not there

---

### Post by nikoPSK on 2007-12-07
Try this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by mgmiller on 2007-12-07
In System > Preferences > Screen Resolution  try selecting a different refresh rate.

Some CRT's are very sensitive to refresh rates and look great at one and crummy at another.

---

### Post by rexxxlo on 2007-12-07
ahh x org i was wondering about that it didnt have the correct video card it seems better now thanks


i will mark this solved

---

### Post by rexxxlo on 2007-12-14
well i thought it was solved but its back again

so i tried xorg again , it will let me choose 1024x786  at 70 hz but when i go to the gui it will only allow 50-55 hz 

the setup in my monitor tells me70 hz

am i missing something?

---

