---
title: "Ubuntu Freezes at splash screen"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-07
Hi
I would like to know if anyone could help me, Ubuntu kind of freezes after etnering username and password, at splash screen. The window and the sound does not appear as usual and instead, after a few seconds, a gray square appears at the left upper part of the screen and if you move the cursor over there the cursor changes to the shape that it adquires in a text enter part.

Please I've been searching over the web and here and I can't find any solutions.
Does anyone has any idea of what is or how to solve it?

---

### Post by nanotube on 2007-05-07
well, what did you do in the previous boot that changed any kind of settings? did you change your gnome config in any way? did you install any software? did you play with firewall settings or put up any servers... ?
"freeze" problem is generic enough that it's hard to say what exactly is causing it.

---

### Post by Jorge32 on 2007-05-07
I installed some drivers of my Wireless Card, but they even didn't worked out, when I rebooted they worked even at the login screen but now it does not enter.

---

### Post by nanotube on 2007-05-07
hmm, well, i can't think of anything but that it could be some corrupted gnome config file.
try renaming your ~/.gnome2 directory to something like ~/.gnome2-bak, and then reboot again and see if it logs in. 

you can do that if you go to a virtual console with ctl-alt-f2, and use the terminal.

---

### Post by calraith on 2007-05-07
Hola Jorge,

I would check to see whether there's something buggered in your /home/jorge or whatever.  When you boot Ubuntu and get to the authentication dialog, hit Ctrl-Alt-F1 to get to a console.  Log in there.

Rename your home directory and let Ubuntu generate all new settings for you next time you log in.  To do this, type the following:
```
sudo killall -9 gdm
```When GDM is killed, hit Alt-F7 to switch back to X, then Ctrl-Alt-Backspace to kill X.  Back at the console, type the following:
```
cd /home
sudo mv $(whoami) $(whoami)-backup
sudo mkdir $(whoami)
sudo chown $(whoami):$(whoami) $(whoami)
sudo gdm
```You can substitute your username wherever you see $(whoami) if you want, or it'll work just as well as-is.

One suspicion I have is that gnome-panel behaves a little strangely when you run Beryl on legacy NVidia drivers, intermittently creating an unclosable box as you describe upon logging in on a couple of machines I've installed it on.  That box has never interfered with anything for me, though.  Gnome continues to load as normal, and I can move the little crashed box to an extremity of the screen where I no longer notice it.  If it turns out that Beryl + NVidia + Gnome is what's freezing your session, try Compiz instead of Beryl.

---

### Post by Jorge32 on 2007-05-07
I don't have and Nvidia card or Beryl. I have an ATI Radeon Xpress 1150 but anyway I'll try your recommendations, let's see if it works

---

### Post by Jorge32 on 2007-05-07
> **calraith said:**
> 

Rename your home directory and let Ubuntu generate all new settings for you next time you log in.  To do this, type the following:
```
sudo killall -9 gdm
```When GDM is killed, hit Alt-F7 to switch back to X, then Ctrl-Alt-Backspace to kill X.  Back at the console, type the following:
```
cd /home
sudo mv $(whoami) $(whoami)-backup
sudo mkdir $(whoami)
sudo chown $(whoami):$(whoami) $(whoami)
sudo gdm
```You can substitute your username wherever you see $(whoami) if you want, or it'll work just as well as-is.



this didn't work because it said that mv and mkdir had error, by telling $(whoami) you mean $jorge? (in case jorge is my user), because, it does not works....

---

### Post by calraith on 2007-05-07
Yeah, just use jorge instead of $(whoami).  After killing gdm and X, do:
```
cd /home
sudo mv jorge jorge-backup
sudo mkdir jorge
sudo chown jorge:jorge jorge
sudo gdm
```

---

### Post by Jorge32 on 2007-05-07
It didn't worked out... again, after enterwing password, when it appears to be loading the square appears and it just freezes over there.

---

### Post by Jorge32 on 2007-05-07
> **nanotube said:**
> hmm, well, i can't think of anything but that it could be some corrupted gnome config file.
try renaming your ~/.gnome2 directory to something like ~/.gnome2-bak, and then reboot again and see if it logs in. 

you can do that if you go to a virtual console with ctl-alt-f2, and use the terminal.

By the way i tried with it but i really forgot too much things about ubuntu, how do you make this from the terminal ?  :$.....

---

