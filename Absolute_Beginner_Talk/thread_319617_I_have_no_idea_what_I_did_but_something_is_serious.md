---
title: "I have no idea what I did but something is seriously wrong..."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-12-15
Well I started up my computer last night and it booted normally as if it were going to go to my desktop. Well now, when I boot it up it goes into this shell type thing. It asks me to log in and I do but it only takes me to a thing somewhat like the terminal that is all through commands... I really have no idea what's going on.  I'm using dapper by the way.

---

### Post by taurus on 2006-12-15
Did you happen to update your machine at all?  What happens if you type this at the prompt?

```
startx
```

---

### Post by voodoonirvana on 2006-12-15
> **taurus said:**
> Did you happen to update your machine at all?  What happens if you type this at the prompt?

```
startx
```

Ummmm yeah I did update it I'm pretty sure. I did something with the alsa. Like deleting it and then reinstalling it. So I did that command and now its just in this like blank yellowish screen not doing anything...:confused:

---

### Post by taurus on 2006-12-15
<Ctrl><Alt>Backspace to exit X and at the prompt, try to install Gnome again!!!

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by voodoonirvana on 2006-12-15
> **taurus said:**
> <Ctrl><Alt>Backspace to exit X and at the prompt, try to install Gnome again!!!

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

Okay the CTRL ALT BACKSPACE thing didnt work so I had to reboot. But it worked!:-D  Now am I going to have to do this EVERY time I boot now? I really hope not.

---

### Post by taurus on 2006-12-15
> **voodoonirvana said:**
> Okay the CTRL ALT BACKSPACE thing didnt work so I had to reboot. But it worked!:-D  Now am I going to have to do this EVERY time I boot now? I really hope not.

You have to do what every time you boot!!!  :confused:

---

### Post by jimrz on 2006-12-15
> **voodoonirvana said:**
> Okay the CTRL ALT BACKSPACE thing didnt work so I had to reboot. But it worked!:-D  Now am I going to have to do this EVERY time I boot now? I really hope not.

shouldn't...ought to be back to normal operation now that it worked for you

---

### Post by voodoonirvana on 2006-12-15
> **taurus said:**
> You have to do what every time you boot!!!  :confused:

[B]sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start[/B]

This!? Logically, I wouldn't think this is going to happen every time I boot now, but I just have to make sure. Did I fix the problem or what?:confused:

---

### Post by cborga1985 on 2006-12-15
> **voodoonirvana said:**
> Okay the CTRL ALT BACKSPACE thing didnt work so I had to reboot. But it worked!:-D  Now am I going to have to do this EVERY time I boot now? I really hope not.

if you mean reinstall gnome. the answer should be no. also, when you reinstalled gnome with the command above, it should have corrected whatever was wrong. it is possible that something might still be broke though.

---

### Post by voodoonirvana on 2006-12-15
> **cborga1985 said:**
> if you mean reinstall gnome. the answer should be no. also, when you reinstalled gnome with the command above, it should have corrected whatever was wrong. it is possible that something might still be broke though.

Thankyou. I thought this was going to be a bit more serious. Sorry for the overexaggurations.

---

### Post by cborga1985 on 2006-12-15
> **voodoonirvana said:**
> Thankyou. I thought this was going to be a bit more serious. Sorry for the overexaggurations.
no problem

---

