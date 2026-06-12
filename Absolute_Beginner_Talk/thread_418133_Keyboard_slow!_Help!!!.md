---
title: "Keyboard slow! Help!!!"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Charco on 2007-04-22
Ok, this is really weird. it works but I need to hold each key for two seconds for letter to come out. (windows decoration flashes once each time key is pressed. no problems in login screen. even occurs on failsafe gnome. Help!!!

ran reconfigure xorg. no luck

---

### Post by freebird54 on 2007-04-22
Need to know more (sorry).  Ubuntu Version (#.## is ok) - is keyboard PS/2, USB, what?  When did it start.  What did you last do :)  We'll see what we can come up with...

---

### Post by Charco on 2007-04-22
just upgraded to Fiesty. Wireless logitech keyboard w/ ps2 adapter. was trying to get beryl to work when it happened. 

Doing this might have broke it? i removed it but no luck
> 

First change gdm.conf-custom:

$ sudo nano /etc/gdm/gdm.conf-custom

Go to the very bottom of the file and add:

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

When you reboot or restart the graphical session, the Xgl server should be running. 

---

### Post by freebird54 on 2007-04-22
I have seen X, the main system, nd XGL have different ideas of what the keyboard is defined as before.  If you can cancel the loading of XGL - that would be the first step.  If not, then post the output of 

cat /etc/X11/xorg.conf

to the forum (after paste, highlight the text, and click # above to 'put it in a box')

Kind of a weird one.

PS - sorry for slow respose - despite the tag line, I *DO* need sleep :)

---

### Post by freebird54 on 2007-04-22
Is there any chane that 'Slow Keys mode' got enabled in System->Prefereces->Keyboard?  don't know how it would - but another place to check... :)

---

### Post by freebird54 on 2007-04-22
Here are some other suggestions from the 'cloud'.

```
Check that the 'rat and kbd are not plugged in to each other's connectors'
```

```
Change the connection to USB
```

```
'Reboot - and it went away'
```

Hope that one of those helps - while the search continues....

---

### Post by Charco on 2007-04-23
Thank you so much for your help, but nothing seems to work. :(
I've tried all day and I've given up. I'm just gonna reformat. This is just too annoying.
Thanks again for all your help. I really do appreciate it. Have a great day!

---

