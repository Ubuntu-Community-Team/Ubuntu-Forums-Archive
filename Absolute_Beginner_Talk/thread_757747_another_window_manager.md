---
title: "another window manager"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-17
Hello

i wondered if anybody knows about window managers?

recently i installed Ubuntulite.....it uses the Openbox window manager.

i wonder if it is possible to  put another WM on my system?...i want to use window maker...

sudo aptitude install wmaker

how would i get window maker to start up at login?....i am not sure that it appears as an option?

thanks


Vince.

---

### Post by kellemes on 2008-04-17
Do you use GDM or KDM (a graphical windowmanager)?
In that case you can choose your windowmanager from the Session-button in your loginscreen.

---

### Post by vinceUUUU on 2008-04-17
Hello

uh....not sure what Ubuntulite uses....GDM or KDM login screen

hmmmm

Vince.

---

### Post by sanus|art on 2008-04-18
Don't know about ubuntulite, but I use GNOME and FluxBox (as seperate managers) - both are present for selection in the session menu.

---

### Post by eriqjaffe on 2008-04-18
IIRC, Ubuntulite uses SLiM as the login manager - you need to hand-configure that to add sessions, but it's possible.

The SLiM configuration file is /usr/etc/slim.conf, (or maybe /etc/slim.conf, I'm not sure - wherever it is, it's slim.conf).  Look for this section and edit accordingly:

```
...
# Command run on login
login_cmd       exec /bin/bash - ~/.xinitrc %session
...
# Specify sessions here
sessions            GNOME,KDE,XFCE4,ICEWM,FLUXBOX
```

...and you add the sessions to  ~/.xinitrc.  For example:

```
#!/bin/bash
DEFAULTSESSION=startxfce4
case "$1" in
        "GNOME")
                exec gnome-session
                ;;
        "KDE")
                exec startkde
                ;;
        "XFCE4")
                exec startxfce4
                ;;
        "ICEWM")
                exec icewm-session
                ;;
        "FLUXBOX")
                exec startfluxbox
                ;;
        *)
                exec $DEFAULTSESSION
                ;;
esac
```

...obviously, your files would reflect whatever WM/DEs you have installed.  When you're at the login screen for SLiM, press F1 to cycle through the available sessions.  This procedure works just fine on my laptop.

---

### Post by vinceUUUU on 2008-04-18
Hello

thanks very much..

wanted to try window maker WM.... with Ubuntulite....and also the DE called "openlook"... 

and maybe "enlightenment" aswell

[http://en.wikipedia.org/wiki/OpenWindows](http://en.wikipedia.org/wiki/OpenWindows)  (bottom of screen openlook)

do you think they will work?

i know ubuntulite already uses ROX filer...and openbox...

there are several DE's i want to try...like EDE (equinox DE) and others...

thanks

Vince.

so after......... /.xinitrc...........do i type 

#!/bin/bash
DEFAULTSESSION=startxfce4
case "$1" in
            "GNOME")
                exec gnome-session
                ;;
            "KDE")
                exec startkde
                ;;
            "XFCE4")
               exec startxfce4
                ;;
            "WMAKER")
                exec wmaker-session
                ;;
            "OPENLOOK")
               exec Openlook-session



and so on and so on?.....i understand that some may already be there....but what about adding a DE?....is it the START command or the SESSION command

do you think it will work?

thanks

Vince.

---

### Post by vinceUUUU on 2008-04-18
Hello

this may sound ridiculous..but how do you use this FORUM?

how do you list and find your own threads....to read them?

thanks

Vince.

---

### Post by kellemes on 2008-04-18
> **vinceUUUU said:**
> Hello

this may sound ridiculous..but how do you use this FORUM?

how do you list and find your own threads....to read them?

thanks

Vince.

[http://ubuntuforums.org/showthread.php?t=726219]("http://ubuntuforums.org/showthread.php?t=726219")

---

### Post by vinceUUUU on 2008-04-18
Hello

thanks for your reply about how to effectively use this forum.

Vince.

---

### Post by eriqjaffe on 2008-04-18
> **vinceUUUU said:**
> so after......... /.xinitrc...........do i type 

#!/bin/bash
DEFAULTSESSION=startxfce4
case "$1" in
            "GNOME")
                exec gnome-session
                ;;
            "KDE")
                exec startkde
                ;;
            "XFCE4")
               exec startxfce4
                ;;
            "WMAKER")
                exec wmaker-session
                ;;
            "OPENLOOK")
               exec Openlook-session



and so on and so on?.....i understand that some may already be there....but what about adding a DE?....is it the START command or the SESSION commandDepends on the WM or DE you're trying to run, each one should have information on starting it in its documentation.

Obviously, if you don't have GNOME or KDE installed, you should remove the lines in the ~/.xinitrc file so you don't try starting an environment that doesn't exist.  ;)

---

### Post by vinceUUUU on 2008-04-18
Hello

ok ....thanks for that..

it seams that window maker tends to work fine in Ubuntu...maybe it will be fine if i add those lines in Ubuntulite..

i know that a DE is different from a WM...maybe the DE needs the session command as opssed to the start command...

openlook is a DE...

i want to try these DE's because university campus still use the CDE desktop in unix....... and also open windows and openlook desktops...

there are others too..unix based DE's that work inside Linux..

thanks

Vince.

---

### Post by jviscosi on 2008-04-18
> **vinceUUUU said:**
> Hello

thanks very much..

wanted to try window maker WM.... with Ubuntulite....and also the DE called "openlook"... 

and maybe "enlightenment" aswell

[http://en.wikipedia.org/wiki/OpenWindows](http://en.wikipedia.org/wiki/OpenWindows)  (bottom of screen openlook)

do you think they will work?

i know ubuntulite already uses ROX filer...and openbox...

there are several DE's i want to try...like EDE (equinox DE) and others...

thanks

Vince.

I've never had trouble with an alternative window manager not working in Ubuntu. When installed from the repositories, they set themselves up in the login manager automatically so you can choose them as a session. Not sure how it works in Ubuntulite though.

I've tried EDE; It lets you party like it's Windows 95.  You may have to try a bunch of WMs and DEs before finding the one that fits.  FWIW, I usually use Fluxbox, Openbox, or Window Maker.

---

### Post by vinceUUUU on 2008-04-18
Hello

yeah...window maker is good...in my humble opinion...

it is good to use....and fast...

yes...window managers have no problem with ubuntu....

i expect with a little tpying of my own...ubuntulite will be the same story...

going to try openlook DE aswell....because it is like university campus...and also the CDE desktop environment ...

V.

---

