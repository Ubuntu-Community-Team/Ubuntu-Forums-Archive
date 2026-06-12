---
title: "So I install envy and now I get an error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by JohnnyQuickCash on 2007-07-04
Once I installed drivers from envy it said something was wrong with the x serve configuration. Can I fix it so I dont have to format?

---

### Post by silent1643 on 2007-07-04
can you uninstall the drivers envy installed?

---

### Post by JohnnyQuickCash on 2007-07-04
Thats kinda what I want to do. What would the command be?

---

### Post by JohnnyQuickCash on 2007-07-04
anyone know?

---

### Post by psyopper on 2007-07-05
Can you boot into your GUI? If so then go to System Tools - Envy. In Envy there is an uninstall button.

I went through this same problem, and I couldn't get X to start (and thus could not get into Gnome) and was left at a terminal (after exiting the various X Server errors). If you are good you can edit your xorg.conf but the easier way is to reinstall X:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.<todays date>
sudo dpkg-reconfigure xserver-xorg

```

Follow the instructions on the screen and when prompted for which driver you want to use select VESA and for now ignore anything specific for your video card. Once it's done it will put you back to a terminal prompt. Now you can start X and get into your GUI to get into Envy and uninstall whatever crap it installed.
```

startx

```

Good luck, and once you get back to where your system is running you should post up just exactly what video card you have, what drivers you want to install and someone will likely be happy to help you do it the right way. 

Envy is the bane of my existence. Not really, but it causes far more problems than none and there are (obviously) safer, if not more difficult methods. I know, as I said, I fell for the Envy script myself.

---

### Post by JohnnyQuickCash on 2007-07-05
I have a 6800 GS and im trying to install the newest drivers I belive with evny. Im just trying to install them so I can play games.

---

### Post by Hobo Joe on 2007-07-05
If you can't get into theGUI, here is how you do it from the command line:

First, run Envy:
```

envy -t

```
Then choose the option that is uninstall current driver, or something to that effect.

Then, click 'manually install drivers, then choose nvidia, then choose version 100.
Once the install has finished, choose YES on the option that asks if you want to reconfigure X.

If you have any questions or problems just post back.

---

### Post by JohnnyQuickCash on 2007-07-05
It kicks me out to a all black screen with typing

---

### Post by bodhi.zazen on 2007-07-05
> **JohnnyQuickCash said:**
> It kicks me out to a all black screen with typing

Not sure where you are at exactly ...

If you DID NOT follow Hobo Joe's advice, start there.

If you DID, well, : enter this command : ```
sudo /etc/init.d/gdm restart
```

Post any error messages ...

---

### Post by JohnnyQuickCash on 2007-07-05
Sweet it worked. Thanks guys.:p

---

