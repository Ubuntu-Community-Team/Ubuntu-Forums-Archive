---
title: "Trying to find my folders (Wine) for use with (Steam)"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by G. Mink on 2007-06-01
um to put this in perspective I have never done anything on a computer so this was a venture of 
 knowledge and first timers trial

I just installed Wine well at least i think I did anyway, I went to
 [http://www.winehq.org/](http://www.winehq.org/)  
then to 
 [http://www.winehq.org/site/download](http://www.winehq.org/site/download) 
then to 
 [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).
  ok from there I opened a terminal and used the commands it told me to add the repositories for APT went something like 
"wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -"  after that I added the next item it told me to enter 
 "sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list"

 it asked for my password both times and after confirming it ran a short loading screen and exited.

I file searched and found it and installed it with Synaptic package manager I still cant seem to do anything with it as far as executing it and configuring it I guess that was my main question =P but I wanted to make sure I didnt do something to fumble it up.

---

### Post by Dev0205 on 2007-06-01
G. Mink,

Are you trying to find the Steam files in Wine? If so, you can find them via Nautilus. Click on your home directory and press "Ctrl-H" this shows all hidden files. Browse down to .wine, then drive_C, Whatever folder you installed Steam in. Most times you can right click the .exe and choose to "Run in Wine". 

Goodluck,
Dev0205

Edit : There really isn't a wine program you load. Usually you just select the program you want wine to run and it does all the work. However, if you want to configure the Wine settings, open the terminal and type > winecfg If that program comes up, wine should be installed.

---

