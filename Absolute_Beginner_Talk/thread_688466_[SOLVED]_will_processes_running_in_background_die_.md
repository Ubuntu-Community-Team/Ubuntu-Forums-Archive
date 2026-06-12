---
title: "[SOLVED] will processes running in background die if I log out?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by quickk on 2008-02-05
Hi everyone, 

   I have a process that I started like this in the terminal:

nohup ./sim &

It's been running for a week (and I probably need it to run for another week).  Will the sim program stop if I restart the x server (for example by pressing CTRL-ALT-BACKSPACE) or if I log out?

Thanks!

---

### Post by doddo on 2008-02-05
Unfortunaly, the answer is yes

however. All things I need running in the background, I put in a screen.

like for example
```
 screen -S rtorrent rtorrent
```
will open up a screen with rtorrent in it, named rtorrent. When Xserver restarts, OR when you hit "CTRL+A then N" It will detach for you to pick up with a
```
screen -dr rtorrent
```
OR
```
 screen -dr
```
if you have only one

screen has a lot of useful features and is a really neat program!

---

### Post by stoodleysnow on 2008-02-05
Or you could just add the program to your startup sessions. System>Preferences>Sessions

---

### Post by doddo on 2008-02-05
> **stoodleysnow said:**
> Or you could just add the program to your startup sessions. System>Preferences>Sessions

But that would mean that program will be killed when your xserver crashes or if your session ends.

Optionally, add the program to /etc/rc.local. I love rc.local. Thats where all the ugly fixes go
```

sudo -s
echo "scripttorunatstart &" >> /etc/rc.local
```

---

### Post by emarkd on 2008-02-05
I second the screen suggestion.  It's great software and you'll find lots of uses for it.  I don't think it's installed by default, but it's in Synaptic if you need it.

---

### Post by quickk on 2008-02-29
Thanks for the info!

---

