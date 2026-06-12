---
title: "Server Install... No GUI?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by mroark on 2006-03-08
I just redid a server install due to limited pc resources.  I am unable to get to the desktop.  I have tried several commands w/ apt-get.  It loads several items, but tells me I'm locked out.  I notice that there are a lot http:\\  in the resources.list 


I have tried:  sudo apt-get xubuntu-xorg and other similar commands.  Startx will go through the sequence of trying to get to the desktop, but I get a screen telling me it could not identify the drivers.

I do not have this pc conncected to the internet is this what is keeping me from getting to the desktop? :-k

---

### Post by Stealth on 2006-03-08
Server installs don't install any GUI tools or X servers. You'll need to download xubuntu-desktop from apt-get if you want XFCE. However, seeing as how you don't have internet, you can't, and probably have to apt-get ubuntu-desktop since then it can read it off the CD (which I assume is still in your sources.list)

---

### Post by mroark on 2006-03-08
If I can get to the internet what will I need to do?  By running the commands with xserver or ubuntu-desktop will this retrieve the data needed?  Thanks for responding!

---

### Post by Stealth on 2006-03-08
All you need for a desktop (if you connect online) is a:
```
sudo apt-get install xubuntu-desktop
```

and that should get you all set up with XFCE and your GUI needs...

---

### Post by mroark on 2006-03-08
[QUOTE=Stealth]All you need for a desktop (if you connect online) is a:
```
sudo apt-get install xubuntu-desktop
```

and that should get you all set up with XFCE and your GUI needs...[/QUOTE]




Thanks!  I'll give it a try!

---

### Post by meborc on 2006-03-08
for more help (guides) on low memory machines and ubuntu refer to: [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

---

### Post by kaamos on 2006-03-08
[QUOTE=Stealth]All you need for a desktop (if you connect online) is a:
```
sudo apt-get install xubuntu-desktop
```

and that should get you all set up with XFCE and your GUI needs...[/QUOTE]

Before that, universe must be in use. Instructions here -> [https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

---

### Post by mroark on 2006-03-08
Thanks guys!

I have utilized both of these commands and nothing beneficial to me happened.  This is what led me to think about being online would make the difference.  

Having already run these commands will I need to rerun them.  I know I'll have to do the ubuntu-desktop, but what about getting the repositories?

---

### Post by deBaas on 2006-03-08
1) check your sources.list file to see it the cd-rom is mentioned here. Make sure it is. 
2)If you have a ubuntu cd just do #sudo apt-get install ubuntu-dektop
3)for kubuntu use kubuntu-dektop.

No need for an internet connection.

---

