---
title: "Installing Kubuntu has left me stuck at a terminal window"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by icarus punk on 2008-03-25
everyone raved about kubuntu, i thought id check it out, i was very disappointed, endless crashing and instability have left me sour.

so now i can't get a desktop i just have a terminal window, ive tried to boot from an XP and NT disc to put this behind me but it won't have it, its just launchs kubuntu and ignores the cd, even though i changed the boot order. can anyone help?

---

### Post by om1 on 2008-03-25
at the command line type this```
sudo apt-get install ubuntu-desktop
```
that will give you back the good old ubuntu desktop

---

### Post by BL00dFox on 2008-03-25
Try this command:

sudo dpkg-reconfigure xserver-xorg while you are in the terminal.

I agree with you for the most part. I like to stick to GNOME, I find KDE to be a bit unstable

---

### Post by icarus punk on 2008-03-25
> **om1 said:**
> at the command line type this```
sudo apt-get install ubuntu-desktop
```
that will give you back the good old ubuntu desktop

that tried to install for 15 minutes got an error, then reset the machine, now im back where i started

---

### Post by icarus punk on 2008-03-25
> **BL00dFox said:**
> Try this command:

sudo dpkg-reconfigure xserver-xorg while you are in the terminal.

I agree with you for the most part. I like to stick to GNOME, I find KDE to be a bit unstable

just tried that and had no idea what i was doing, is there really no way of just formatting the machine from terminal without having to get a desktop?

---

