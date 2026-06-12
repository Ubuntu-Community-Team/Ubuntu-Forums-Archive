---
title: "Problem starting Ubuntu"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by dimovich on 2007-07-05
Everything worked well for 3 months... Today in the morning i booted as usual, entered my username and password, but unfortunately no Gnome "loading bar" has appeared. After a few seconds a window appears with no text on it and nothing happens after that. What should i do?

Thanks.

---

### Post by moredhel on 2007-07-05
Can you say what you did last night? Software and hardware wise. Anything special? Do a software update?

EDIT: Also, if you press ctrl+alt+F1, can you login etc?

---

### Post by dimovich on 2007-07-05
nothing unusual... no hardware or software updates/install. I shut my system down as usual.

---

### Post by dimovich on 2007-07-05
> **moredhel said:**
> 

EDIT: Also, if you press ctrl+alt+F1, can you login etc?

Yes, I can login.

---

### Post by moredhel on 2007-07-05
ok, so login and type startx

---

### Post by dimovich on 2007-07-05
can you please indicate all the commands i should type. i''m using windows now, and would prefer to not boot every 5 minutes to read the next commands i should type :).

What log files should i read to see any possible errors messages?

---

### Post by confused57 on 2007-07-05
> **dimovich said:**
> can you please indicate all the commands i should type. i''m using windows now, and would prefer to not boot every 5 minutes to read the next commands i should type :).

What log files should i read to see any possible errors messages?
If entering the command "startx" doesn't work, then try:
```
sudo dpkg-reconfigure xserver-xorg
```
reconfiguring your xorg.conf may help get you to a gui...

If you've installed nvidia drivers, try "nv" video driver or "vesa"...

---

### Post by dimovich on 2007-07-05
> **confused57 said:**
> If entering the command "startx" doesn't work, then try:
```
sudo dpkg-reconfigure xserver-xorg
```
reconfiguring your xorg.conf may help get you to a gui...

It doesn't help. I must stress that i do have a gui (gdm). After i enter login information there is a small pause, and after that a window appears. It has some text written on it, though it is not displayed (the cursor turns into a caret when i roll it over the window).

---

### Post by confused57 on 2007-07-05
> **dimovich said:**
> It doesn't help. I must stress that i do have a gui (gdm). After i enter login information there is a small pause, and after that a window appears. It has some text written on it, though it is not displayed (the cursor turns into a caret when i roll it over the window).

Maybe "dmesg" will show something:
```
dmesg
```

The output will be relatively long, to print the last 10 lines of the file:
```
dmesg | tail
```

To show the last 20 lines:
```
dmesg | tail -20
```

This might show any error messages...

---

### Post by dimovich on 2007-07-05
> **confused57 said:**
> Maybe "dmesg" will show something:
This might show any error messages...

Thanks! It helped... I (stupid me) remembered that i changed a few things in the iptables startup script, and now I fixed it. Thanks again!

---

