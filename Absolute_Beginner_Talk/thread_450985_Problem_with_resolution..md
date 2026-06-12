---
title: "Problem with resolution."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by leftyguitarjoe on 2007-05-21
My resolution with ubuntu was perfect, but i booted it one day and BAM
600 x 480:mad:

It wont let me pick the resolution to anything higher either. please give me a command for the terminal. I really dont want to re-install ubuntu.

thank you

---

### Post by taurus on 2007-05-21
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You probably need to check the driver for your graphic card.

---

### Post by leftyguitarjoe on 2007-05-21
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070521220643


this it what it said when i tried the command

---

### Post by BarfBag on 2007-05-21
Boot into recovery mode and run the command there.

---

### Post by leftyguitarjoe on 2007-05-21
Same thing happend again...

---

### Post by jerrylamos on 2007-05-21
After you run the 

sudo dpkg-reconfigure -phigh xserver-xorg
enter your password

(note, only blanks in the whole line are between sudo and dpkg, and before -phigh)

can you run

/less/X11/xorg.conf

and see what driver it has in it, and what resolutions?  get out of less by entering: q
for quit.  If the setup looks any better, do 

sudo killall gdm
startx

Not sure what's going on....

Cheers, Jerry

---

### Post by taurus on 2007-05-21
> **jerrylamos said:**
> After you run the 

sudo dpkg-reconfigure -phigh xserver-xorg
enter your password

(note, only blanks in the whole line are between sudo and dpkg, and before -phigh)

can you run

[COLOR="Blue"]/less/X11/xorg.conf[/COLOR]

and see what driver it has in it, and what resolutions?  get out of less by entering: q
for quit.  If the setup looks any better, do 

sudo killall gdm
startx

Not sure what's going on....

Cheers, Jerry

I assume you mean

```
less /etc/X11/xorg.conf
```

---

