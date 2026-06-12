---
title: "gui lost"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Emasters on 2006-10-01
I have lost my gui interface.  when ubuntu boots it goes directly to a command prompt and then I don't know how to load a gui?  Thanks

---

### Post by bulldog on 2006-10-01
Did you see a blue screen about X-server as well?

If not type ```
/etc/init.d/gdm restart
```
to restart Gnome [could be possible you have to use sudo]

---

### Post by jISh on 2006-10-01
What happens when you type the following?
```
startx
```

---

### Post by Emasters on 2006-10-01
I get a grey screen with an x in the middle which is controled by the touch pad.  in the uppe left hand corner i get a terminal window which is just like i had befoe

---

### Post by bodhi.zazen on 2006-10-01
> **bulldog said:**
> Did you see a blue screen about X-server as well?

If not type ```
/etc/init.d/gdm restart
```
to restart Gnome [could be possible you have to use sudo]

Hi Bulldog.

FYI: Yes you need sudo.

You can also```
sudo gdm
```

> **Emasters said:**
> I have lost my gui interface.  when ubuntu boots it goes directly to a command prompt and then I don't know how to load a gui?  Thanks

What have you been playing with? Have you been running as root?

What do you get when you enter:```
which gnome-session
```

---

### Post by Emasters on 2006-10-01
I get nothing... the command prompt takes the command doesn't record any error message but i have no response.  same when i type in the other commnands suggested

i was playing in synaptic trying to load libraries for mplayer when i hit apply it started removing all the "g" apps like gedit, etc.  when synaptic ended I had a very clean desktop and application list and mplayer did play music.  however when i rebooted i got this problem, no gui.... when i put in the ubuntu desktop cd i hang up on the ubuntu logo screen.

---

### Post by bodhi.zazen on 2006-10-01
> **Emasters said:**
> I get nothing... the command prompt takes the command doesn't record any error message but i have no response.  same when i type in the other commnands suggested

i was playing in synaptic trying to load libraries for mplayer when i hit apply it started removing all the "g" apps like gedit, etc.  when synaptic ended I had a very clean desktop and application list and mplayer did play music.  however when i rebooted i got this problem, no gui.... when i put in the ubuntu desktop cd i hang up on the ubuntu logo screen.

Sounds like you removed a bunch of Gnome.

Boot from HD, log in, and try:
```
sudo aptitude install ubuntu-desktop
```

This may break your sound...

---

### Post by Emasters on 2006-10-01
Thanks but I get a resolviing dependencies.....no solution ound in alloted time try harder? I did and still no luck....i am begining to dispair

---

### Post by bodhi.zazen on 2006-10-01
Do you have all your repositories enabled?

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Emasters on 2006-10-01
How do I check,d then how do I enable them, I am lost without the GUI inerface remember! Thanks

---

### Post by bodhi.zazen on 2006-10-01
> **Emasters said:**
> How do I check,d then how do I enable them, I am lost without the GUI inerface remember! Thanks
Sorry:

```
sudo nano /etc/apt/sources.list
```

Remove the # marks from the front of the repositories.

[Like this](http://ubuntuguide.org/wiki/Dapper#Repositories)

Ctrl-X to exit, Y to save your changes.

```
aptitude update
aptitude intall ubuntu-desktop
```

---

### Post by bulldog on 2006-10-01
Offtopic.

---

### Post by bodhi.zazen on 2006-10-01
Thank's Bulldog :) #-o

Too many threads, too many children.

I'll try to edit my previous.

---

