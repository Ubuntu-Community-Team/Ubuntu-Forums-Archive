---
title: "What is going on ? Need HELP !!!!!!!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-09-08
Big problem!!!! HELP!! 

--------------------------------------------------------------------------------

Now I've really got a big trouble. The problem is that when I'm opening a window, for an example the terminal, then when i click anywhere in the window or on minimize or close then the window is minimixed(it's the same for all windows/programs) and then when i click the mouse again anywhere on the desktop or somewhere to launch a new program the first program pops up again. And no new program comes. It bagan doing it just after I was in ccsm(compiz fusion manager). I was playing with the window zoom enchanting(or what its called) and then i did the command SUPER+V as it said to see what happened and then since that it has been doing the thing with the windows. I've tried booting up without compiz fusion in the session list, but to no good, and when im booting up and im where i need to write my username and password, then i cant use the mouse either. I tried to go down and open another session but couldt do it because of this weird problem. So now I'm desperately needing help to fix this. Cant use Ubuntu bacause of it. So i'm in XP.(good that i'm dual-booting) i have no sound either

If i haven't desriped good enough what the problem is then please ask. I really need help!

---

### Post by nonewmsgs on 2007-09-08
if it's a usb mouse with a minidin connector try taking off the connector and trying it straight in the usb.

---

### Post by czepluch on 2007-09-08
> **nonewmsgs said:**
> if it's a usb mouse with a minidin connector try taking off the connector and trying it straight in the usb.

The problem is not connected with the mouse. I've even tried unpluggin the mouse and just using touchpad, still doesn't work.

---

### Post by czepluch on 2007-09-08
Please guys. Really need help!!!!

---

### Post by czepluch on 2007-09-08
bump

---

### Post by bodhi.zazen on 2007-09-08
OUCH ....

I do not know the solution, but as a work-arround, try creating a new user on Ubuntu 

boot to recovery mode and at the command line type "startx" without the quotes

give the new user access to the admin group (for sudo)

You can then try deleting some of the vaious . files in you old users home and re-try the old user.

.gnome2
.nautilus
.gnome

etc

---

### Post by czepluch on 2007-09-08
> **bodhi.zazen said:**
> OUCH ....

I do not know the solution, but as a work-arround, try creating a new user on Ubuntu 

boot to recovery mode and at the command line type "startx" without the quotes

give the new user access to the admin group (for sudo)

You can then try deleting some of the vaious . files in you old users home and re-try the old user.

.gnome2
.nautilus
.gnome

etc

Thanks, but this doesn't seem to help. But I'm very glad that you at least try to help me. I'm desperately needing help. Cant use my Ubuntu :(:(:(

---

### Post by diatribe on 2007-09-08
can you replicate the behaviour on any other environment, like kde or xfce?

---

### Post by Amazona aestiva on 2007-09-08
This is unusual. Reinstalling Ubuntu MIGHT help You... very strange:confused:

---

### Post by czepluch on 2007-09-08
> **diatribe said:**
> can you replicate the behaviour on any other environment, like kde or xfce?

I've got KDE installed as well but its the same behavior. I really have no idea of what is going on ?

---

### Post by schorsch on 2007-09-08
Uhm, I do not use compiz but is there a folder called ".compiz" or something like this in your home directory? Then you can move it to something like "compiz.org", logout, login again and check if the problem still exists.

---

### Post by czepluch on 2007-09-08
> **schorsch said:**
> Uhm, I do not use compiz but is there a folder called ".compiz" or something like this in your home directory? Then you can move it to something like "compiz.org", logout, login again and check if the problem still exists.

Haven't tried it yet, but as i wrote in the first thread it already begins to do it before i sign in to my account. when you have to log in and i've got the option to press the configure button down in the left corner, i cant press it.

---

### Post by schorsch on 2007-09-08
So there seems to be a problem with your xserver config? Type "CTRL-ALT-F1" at the same time and you will get to a text console. Login as your user and try to move any ".compiz*" folder in your $HOME as I mentioned before.
Make a backup of the file /etc/X11/xorg.conf and try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by czepluch on 2007-09-08
> **schorsch said:**
> So there seems to be a problem with your xserver config? Type "CTRL-ALT-F1" at the same time and you will get to a text console. Login as your user and try to move any ".compiz*" folder in your $HOME as I mentioned before.
Make a backup of the file /etc/X11/xorg.conf and try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks. I will try that after the very important football match: Sweden - Denmark. GO DENMARK !!!

---

### Post by czepluch on 2007-09-08
My .compiz folder is gone :S Could anyone just post me the command to unistall compiz fusion ?

---

### Post by Fornax-101 on 2007-09-08
sudo apt-get remove compiz

---

### Post by czepluch on 2007-09-09
somehow it's working now but i didn't do anything. I only found out that the problem appears when I use my usb-mouse. Why is that?

---

### Post by czepluch on 2007-09-09
But the weird thing is that i've been using my mouse for a week without any problems.

---

### Post by czepluch on 2007-09-12
I still can't use my mouse. Is there a way I can get it to work ?

---

