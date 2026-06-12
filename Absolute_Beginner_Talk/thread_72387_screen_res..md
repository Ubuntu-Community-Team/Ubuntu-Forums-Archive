---
title: "screen res."
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by natman on 2005-10-06
hi i am just after linking ubunt up to the internet and got a whole lode of updates, anyway after this i booted up in ubuntu and for some resason the screen res is locked at 640x480 , and i am given no other opions for refresh rate and res.

I have a 17" wide screen laptop so i would like something like 1024x780 , 

Can anyone help?

---

### Post by matthewv on 2005-10-06
[QUOTE=natman]hi i am just after linking ubunt up to the internet and got a whole lode of updates, anyway after this i booted up in ubuntu and for some resason the screen res is locked at 640x480 , and i am given no other opions for refresh rate and res.
I have a 17" wide screen laptop so i would like something like 1024x780 , 
Can anyone help?[/QUOTE]

Does ctrl+alt++ (thats ctrl, and alt, and the + key) give you a higher resolution??
If not, you'll probably have to edit your xorg.conf file.

---

### Post by natman on 2005-10-06
[QUOTE=matthewv]Does ctrl+alt++ (thats ctrl, and alt, and the + key) give you a higher resolution??
If not, you'll probably have to edit your xorg.conf file.[/QUOTE]

Just incase that fails can you tell me how to edit the xorg.conf file?

---

### Post by matthewv on 2005-10-06
There is no harm in trying ctrl+alt++ because it just cycles through the available resolutions... can't hurt... press it again, it changes res agian, press it again, and it changes again... etc..

I'll get back on the xorg.conf...

---

### Post by natman on 2005-10-06
yep just after trying the "ctl alt +" the reolutions did not change even once.

Thanks for that trick though.

---

### Post by matthewv on 2005-10-06
I've never edited xorg.conf before, but here's how I think it's done. Be careful though, as it could break things if you make a mistake.
First, back up your existing xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then open the xorg.conf for editing:
```
sudo gedit /etc/X11/xorg.conf
```
Find the line that reads 
```
Section "Screen"
```
Below this you'll find some lines that read 
```
Modes     "800x600"  "640x480"
```etc...
Add "1024x768" to the front so it reads
```
Modes     "1024x768"  "800x600"  "640x480"
```
Save and then restart x (logout and back in).

Hope that works as I'm no expert here, if I'm wrong hopefully someone will correct me. If that doesnt work a reconfiguration of X might work.
Do this by first backing up your xorg.conf file as above. Then press ctrl+alt+F1 to go to a terminal. Then type
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm stop
```

then restart:
```
sudo reboot
```

If that don't work, well, I'm:confused:

---

### Post by natman on 2005-10-06
i tried what you said above but it doesnt even seem to be able to find /etx/X11/xorg like it doesnt exist.

Maybe i should reinstall
Anyway thanks for the help.

---

### Post by matthewv on 2005-10-06
try searching for xorg.conf on Filesystem

by the way... are you using hoary or breezy???? I don't konw whether the above instructions are valid for hoary, as I'm running breezy...

---

### Post by patrick295767 on 2005-10-06
I usually use the : 
sudo dpkg-reconfigure xserver-xorg

set only one screen I want 
and then u can select :
simple  (screen size)
medium  (choose ur resolution)
> expert  (lot of to set up) <

---

### Post by natman on 2005-10-06
yeah i looked for it on the file sys nothing there, but i am using wathy, and by mistake i used the intel version instead of amd ( i have a 64 amd) set up disc.

is it prob best to reintall with hoary?

---

### Post by matthewv on 2005-10-06
[QUOTE=natman]yeah i looked for it on the file sys nothing there, but i am using wathy, and by mistake i used the intel version instead of amd ( i have a 64 amd) set up disc.

is it prob best to reintall with hoary?[/QUOTE]

I think warty uses X11R6, not X.org... so that would be a heap different to my system. the config file will look similar, but will be called X11.config or something along that line... I havent' used X11 for a while. I would either install hoary or wait a week for the final release of breezy and install that... breezy has much better hardware detection

breezy picked up my graphics card straight off, while it took me a few hours to get it working in hoary

---

### Post by natman on 2005-10-06
ok then thks i think i will wait  aweek for the final releae of badger (amd version) hope everthing works with that.

Thanks for all the help

---

### Post by matthewv on 2005-10-06
No problem... hope breezy will work for you:)

---

### Post by helmethedd on 2005-10-06
system>preferences>screen resolution works for me in hoary. try that.

---

