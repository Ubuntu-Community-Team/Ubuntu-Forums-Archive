---
title: "black screen instead of solash in ubuntu"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by andrewlion on 2007-09-23
first of all i'm not very good at english because i'm spanish

I'm not very good with ubuntu, i had only used it for a week.

yesterday i tryed to install a new splash in my ubuntu sistem, when i reboot mi pc then it apears a black screen.

i wait for hours and then i search in internet for help but i didn't find anything helpfull.

y press ctrl + alt + f1 and then my computer go to the terminal, i'm not very good with it.

please can enyone help me, i can explain it a bit better if you need

thanks

---

### Post by jamvegan on 2007-09-23
If you can describe what you did to install the new splash screen, we can probably help you reverse it in the terminal.  Also, do you get a solid black screen, or do you get any error messages?  If there are messages, posting those would also help.

---

### Post by jjmcgee on 2007-09-23
I also have this problem, had it with Ubuntu 7.04 and now on Kubuntu 7.10.
If I boot using default system boot it gets as far as loading the kubuntu screen then goes to a black screen.
If I then change boot parameter to remove quiet splash, I can see it gets as far as loading the K display manager and it is this point it goes to the black screen. I cant press any keys (caps etc) or ctrl + alt + del or F1, etc. To get out of it I need to switch off.

When I try to boot into rescue mode I get to the console but when I try and type telinit 3 to boot into a command prompt, it loads the relevant stuff and hangs at same black screen.

Any suggestions?

---

### Post by andrewlion on 2007-09-23
First of all I went to the program to download aplications. I search for splash and i download de aplication of splash. then i went to the aplication (in administrate) and i use a image of  


then I shut down the computer, the next day was the problem when i tried to open ubuntu

P.D. there are no messages. first it apears ubuntu, loading. then the mouse change to a clock and the screen become black.

---

### Post by jjmcgee on 2007-09-23
ok I'll try a different topic.. my problem is different from this guy's.
Sorry for invading your post, hope you get the help you need.. :)

---

### Post by jamvegan on 2007-09-23
Okay, one thing that you can try is removing the splash screen package.  You can do that by logging in to the terminal and typing:
```
sudo apt-get remove gnome-splashscreen-manager
```
You will be prompted for your password, and will then be told what will be removed, and asked if you wish to continue.
After apt-get is done, try rebooting and see if it boots normally.  You can reboot from the terminal by typing:
```
sudo reboot
```

---

### Post by alienexplorers on 2007-09-23
Paste this into the terminal you bring up with ctrl-alt-F1:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by andrewlion on 2007-09-24
thank's for your help, i finaly unistal de splash but when i reboot my computer it don't work. I think the splash is not the problem :confused: :confused:

alienexplorers, thanks but when i used that comand, it apears many questions that i'm not able to answer

i don't now what to do now, I think the best is to install ubuntu an other time, can you help me with that, only using the terminal. If it is imposible i will try with te live cd

P.D. If the splash is not the problem it could be the firewall [Firestarter [http://www.guia-ubuntu.org/index.php?title=Cortafuegos]](http://www.guia-ubuntu.org/index.php?title=Cortafuegos])
or the theme becouse that day y try to dowload one and use it (it work's)

thank's for all and i will continue working ;) :(:(

---

