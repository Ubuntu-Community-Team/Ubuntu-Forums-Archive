---
title: "Problem With Ubuntu"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by lenswipe on 2007-12-09
Hi all 

im having a problem with ubuntu....

I just installed it yesterday and it worked fine but when i logged on today everything apeared in 800X600 resolution. Its so big that i cant even click the ok button at the bottom of some of the windows and the places menu takes half the screen up.

A screenshot is enclosed..


PLEASE HELP....


TY IN ADVANCE...

---

### Post by overdrank on 2007-12-09
> **lenswipe said:**
> Hi all 

im having a problem with ubuntu....

I just installed it yesterday and it worked fine but when i logged on today everything apeared in 800X600 resolution. Its so big that i cant even click the ok button at the bottom of some of the windows and the places menu takes half the screen up.

A screenshot is enclosed..


PLEASE HELP....


TY IN ADVANCE...

Hi what is the model of the graphics card? You can try and  when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command startx or to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by lenswipe on 2007-12-09
> **overdrank said:**
> Hi what is the model of the graphics card? You can try and  when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command startx or to reboot ```
sudo reboot
``` Hope this helps and good luck!

forget it i got it sorted through the GUI

something had told Ubuntu that i had a 800x600 monitor (i know, wtf??)


so i had to go and set that back and tell it i had a 1024x768 monitor.

Although to move onto something else....


I try to enable the visual effects in ubuntu and it just says Desktop Effects could not be enabled. I have no graphics card on my machine just the plain old one that came with it. Maybe this is why?

Hope you can help

thanks :p

lenswipe

---

### Post by thiebaude on 2007-12-09
Just to check, System>Administration>Screens and Graphics> to see what graphics card driver you have and then choose your screen resolution in Preferences>Screen Resolution
I hope this works for you.

---

### Post by overdrank on 2007-12-09
Hi and to find your graphics card use the command in the terminal ```
lspci
``` it will be listed with VGA at the beginning of the line. Then to verify your correct driver is being used you can view your xorg with this command ```
cat /etc/X11/xorg.conf
``` then you can search for your model card in the forums and find help. Good luck!

---

### Post by lenswipe on 2007-12-09
> **overdrank said:**
> Hi and to find your graphics card use the command in the terminal ```
lspci
``` it will be listed with VGA at the beginning of the line. Then to verify your correct driver is being used you can view your xorg with this command ```
cat /etc/X11/xorg.conf
``` then you can search for your model card in the forums and find help. Good luck!

:lolflag:

i dont have a graphics card...


apart from the built in intel one :P

here is the results from the first command though

---

### Post by mlentink on 2007-12-09
Would it disappoint you extremely if I were to say your system simply doesn't support advanced graphics?
If so, I'm sorry. But it won't change much...

---

### Post by lenswipe on 2007-12-09
> **mlentink said:**
> Would it disappoint you extremely if I were to say your system simply doesn't support advanced graphics?
If so, I'm sorry. But it won't change much...

it would disapoint me a great deal... :(

is there anything i can do???

:(

---

