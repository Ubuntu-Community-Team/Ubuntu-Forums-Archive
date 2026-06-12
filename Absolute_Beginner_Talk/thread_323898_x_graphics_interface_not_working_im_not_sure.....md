---
title: "x graphics interface? not working? im not sure...."
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by dfk789 on 2006-12-22
Hey guys! :)

So because my personal laptop has no cd drive, i removed the hard drive from my sisters and installed ubuntu that way. Now when i put the hard drive in, it will load most of teh stuff fine until it gets to where it want to go to the login screen, where im presented with the error about x graphical interface or something like that. mentioning somethign about radeon (the graphics chip in my laptop). What to do?

Info the graphics chip is radeon mobililty 7500, laptop ibm thinkpad T30

All help and input welcome thank you! :D

---

### Post by raul_ on 2006-12-22
Try installing the Nvidia drivers. Through the terminal will seem a little hard, but i think you'll be ok. just print these instructions and follow them religiously:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")

---

### Post by riven0 on 2006-12-22
Yeah, but Radeon means ATI. :D 

dfk789, before you do anything why don't you try to reconfigure the xserver. After the error message, hit enter and you should boot up to the terminal. Log in and type:

> sudo dpkg-reconfigure xserver-xorg


Then just keep hitingt enter if you don't know what to input and reboot with:
> 
sudo shutdown -r now

---

### Post by raul_ on 2006-12-22
Oops :rolleyes: my bad. I confused it with geforce. Sorry

---

### Post by dfk789 on 2006-12-23
guys that worked perfectly :D thank you so much! been trying to sort this out fo the past day or so restlessly and yeah i'm extremly fond of you guys atm :p 

Thanks alot for the help :)

---

