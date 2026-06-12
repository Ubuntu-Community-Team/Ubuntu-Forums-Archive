---
title: "installing feisty ????"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-04-04
hi
i just used the 8 mg install to install festy over the internet, everyting seemed to go well no problems no errors . but there is always a but , when i reboot it loads severial things and then with no errors and then it dumps me at a comand prompt . i can log in with user name and password and navagate the files but the desk top doesn't start any ideas ?   i looked for the xorg.conf file but it isn't there i went to /etc/X11 and the only file there is xkb ??????????????

---

### Post by tkjacobsen on 2007-04-04
try to "sudo apt-get install ubuntu-desktop" to install the destop packages. Sounds like you only installed the command line part of the dist.

---

### Post by Mr. Eddy on 2007-04-04
What happens when you type:

```
startx
```

have you installed the desktopversion? maybe you installed the serverversion.
you get no errors?

just an idee, I'm no expert

---

### Post by klein de usa on 2007-04-04
hi
ok typing startx gives me:

the program 'startx' is currently not installed. you can start it by typing: sudo apt-get install xinit 
 
 ok do i do that or do i type "sudo apt-get install ubuntu-desktop" ?   

ok using the minimum iso 8 mb in hit enter at the prompt so it should of been the desk top 

thank you tkjacobsen and Mr. Eddy

---

### Post by zvacet on 2007-04-04
```
sudo aptitude install ubuntu-desktop
```

---

### Post by klein de usa on 2007-04-04
thank you zvacet

i started it 4 hours ago hum lets see 329 files so far, 34% finished 2d 11h 20m, i should of waited for the cd to come out smiling it may take till the 17th to get it down loaded 

thank all for your help

---

