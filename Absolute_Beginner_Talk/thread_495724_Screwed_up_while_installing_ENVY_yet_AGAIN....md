---
title: "Screwed up while installing ENVY yet AGAIN..."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-07-08
Please walk me through this like I'm an idiot.  I am stuck at the command line, can't even get to Gnome.  I don't know what I did.  I went to Alberto Milone's page but I don't understand it.

---

### Post by reset3x on 2007-07-08
Installing Envy is pretty simple... Just download the deb... Double-click on it and GDebi will open and install the package...

---

### Post by bean77 on 2007-07-08
I did this:

```
sudo dpkg-reconfigure xserver-xorg
```

And walked through the options...

---

### Post by reset3x on 2007-07-08
Which driver are you using? And do  you have Envy installed?

---

### Post by bean77 on 2007-07-08
The I get a warning...

overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20070708113534

---

### Post by bean77 on 2007-07-08
> **reset3x said:**
> Which driver are you using?

Nvidia?

---

### Post by Outrunner on 2007-07-08
I don't think you'll need that anymore, so you can overwrite it.

---

### Post by bean77 on 2007-07-08
> **reset3x said:**
> Installing Envy is pretty simple... Just download the deb... Double-click on it and GDebi will open and install the package...

Remember, I am a complete idiot here-please tell me how to download it from the terminal as I cannot even get to the desktop.

---

### Post by bean77 on 2007-07-08
> **Outrunner said:**
> I don't think you'll need that anymore, so you can overwrite it.
OK so what is my next command?

---

### Post by Outrunner on 2007-07-08
What do you "what is my next command", doesn't it ask you any more questions after that? If not, then type 
```

startx
```

to get to your GUI.

---

### Post by bean77 on 2007-07-08
> **Outrunner said:**
> What do you "what is my next command", doesn't it ask you any more questions after that? If not, then type 
```

startx
```

to get to your GUI.


Fatal server error: no screens found...and a ton of text before and after.  (I'm using my hubbie's laptop to do this so if there is anything I should be loking for, let me know so I don't have ogt re-type the whole thing!)

Thanks so much for helping me-I am such a newbie.

---

### Post by Outrunner on 2007-07-08
Found this with Google:

```
XFree86 -configure
```

If that doesn't work, try typing it in all lowercase

```
xfree86 -configure
```

Then try 'startx' again

---

