---
title: "step by step guide to installing belkin wireless desktop card (FSD6001_ver3)"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Sir Frederic on 2005-11-21
i believe this card has a realtek 8180 chip;
i have tried both the belkin driver .inf file and also the one from the realek site but nothing appears to work.
take into account that i amreally new to linux and know virtually nothing so i could have been doing this the wrong way and i really need an every-step-of-the-way type tutorial :) 
i am using ubuntu 5.10.

also ndiswrapper appears to work fine except when i check for installed drivers it always tels me 'no drivers installed' or something like that.

help me please or i may be forced back to windows permanently. :(

---

### Post by janne5011 on 2005-11-21
[QUOTE=Sir Frederic]i believe this card has a realtek 8180 chip;
i have tried both the belkin driver .inf file and also the one from the realek site but nothing appears to work.
take into account that i amreally new to linux and know virtually nothing so i could have been doing this the wrong way and i really need an every-step-of-the-way type tutorial :) 
i am using ubuntu 5.10.

also ndiswrapper appears to work fine except when i check for installed drivers it always tels me 'no drivers installed' or something like that.

help me please or i may be forced back to windows permanently. :([/QUOTE]

I think ndiswrapper is the best choice.
assuming you have ndiswrapper installed do this:
cd to the directory with your .inf files and type in terminal:
sudo ndiswrapper -i thedriver.inf

I guess the problem you try to use terminalcommands but in wrong directory,right?
put the files in  home directory (copy/paste) and type: cd  /home
then: sudo ndiswrapper -i your.inf
then: sudo ndiswrapper -l
works?

---

### Post by Sir Frederic on 2005-11-21
thanks, worked to a point but said the drivers were invalid (see as follows)

fredericthewise@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
eappkt  invalid driver!
net8180 invalid driver!
rtl8180.sys     invalid driver!

and still nothing works, i did all as told and am also told on several websites that the net8180 driver does work (the card is based on that chip):(

p.s. i take a while to get back as i have to boot from ubuntu into windows and vice-versa to access the internet.

---

