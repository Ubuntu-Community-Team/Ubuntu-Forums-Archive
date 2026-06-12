---
title: "[SOLVED] multiple login screens with GDM"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by rnjn.sinha on 2008-04-16
Is it possible to have multiple graphical login screen starting from f7 like we can have multiple console from f1-f6?

--

---

### Post by darksizzle on 2008-04-16
Ummm It doesn't look like it I just gave it a shot on a different display and it told me another gdm was already running.  What are you trying to do are you trying to have multiple user's available or just play around with multiple window managers?  Here's a small example to get you started

I run wmii (a window manager) on my regular :0 display (the default F7) and I would like to run gnome on F8 so I can toggle between the two.  Here's what I would do-

First install sux, it's available is aptitude and all it is is a bash script that passes your Xorg credentials to another user.  So in the console:
```
sudo aptitude install sux
```

Now go to one of the 6 available tty's it doesn't matter but you're going to need to remember which one you started working from

login, then start a sudo session ```
sudo -s
``` in the selected console

Once you're root type in this command
```
Xorg :1 vt8 &
```

This is going to start a new X session using the display :1 (:0 is already taken by your default X) on virtual terminal 8 (F8) and background it so you can keep using the console you're working from.  It's going to pull your focus away from your console and onto the new Xorg on vt8 so once it loads up jump back to the tty you selected.

Now you need to set the DISPLAY variable so your console will know where to direct graphical applications to
```
export DISPLAY=:1
```

Now login to the user you'd like to run the new gnome session as with sux to pass through your new X credentials
```
sux youruser
```

type in ```
gnome-session
```

and go to vt8, gnome should be starting up

Again let me know what you're trying to do if you need help

---

### Post by rnjn.sinha on 2008-04-16
Hey thanks a lot. This indeed solves my issue. Actually I have two machines. a laptop and a desktop with dual monitor support. I could login remotely to the laptop and get its session to my other machine using ssh forwarding but this would eat up the available screen. Now using the steps that you have provided, I have (on virtual terminal 7) gnome session of my laptop and on vt8 I have the original XFCE session of my desktop.  :guitar: 

Thanks a ton for your help.

---

