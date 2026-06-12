---
title: "How To Run GUI Programs From Terminal?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-20
Hi I'm helping my dad setting up an old IBM Thinkpad 240 laptop an dI have so far installed the Debian distro on it with everything that comes with it. OpenOffice, Rhythmbox, Evolution etc. and its kinda hard for the laptop to cope with all that.

The idea is to uninstall Gnom and just run everything from the command line. He only needs to programs anyway, and that for streaming music from his desktop which Rhythmbox does perfect and then an internet browser. He doesn'ti need the desktop environment.

So until he gets familiar with the command line we will keep the GUI but how would he go about running a GUI like rhythmbox from the commandline when the gdm is stopped. What I have tried so far is.
from terminal logged in to Gnome:
```
su -
passwword:
/etc/init.d/gdm stop
```
and then the gdm stops and I'm ready to start in the command line, but when I type
> rhythmbox
nothing happens, and I was hoping that it would start so that I could run it and safe some RAM.

---

### Post by pbaehr on 2007-07-20
I don't think you can run GUI programs without a window manager. Have you considered Xubuntu for a lighter window manager instead? Or maybe iceWM?

---

### Post by Lord_Dicranius on 2007-07-20
Gnome is a desktop environment.  As far as I know,  you need some type of desktop environment (Gnome, KDE, etc) to run GUI appliactions.  I'd go with pbaehr's recommendations.

---

### Post by Ev.Eli on 2007-07-20
Technically, you don't need a desktop environment, or even a window manager to run GUI programs. You do however need the X Window system, and many programs are simply unusable without a window manager. As others have mentioned, I would recommend checking out Xubuntu, because it is fairly lightweight. If you really must avoid DEs altogether, you could throw together a GDM session with Fluxbox or something, but I really don't recommend it. Trust me, extreme minimalism isn't nearly as friendly as you think it is.

---

### Post by eternalsword on 2007-07-20
fluxbox beats gnome/kde in my book, reasons being it's lighter on resources and no limit to number of configurable system hotkeys, but it's true that minimalism isn't for everyone.  To each his own.

---

### Post by kasperbs on 2007-07-20
Well it does sound interesting trying anither desktop environment, and I have tried Xubuntu on another laptop of mine, but didn't like it much.

Basically what I want to archieve is that whenever my computer is turned on it automatically starts up (no need) to log in or anything and starts up rhythmbox in fullscreen and nothing else. (except the network so I can stream the music)
This is because it needs to as easy as possible and should take long to start up as it will take too long compared to turn on the cd player and the point is gone then if it's too much hassle, and my dads wife wouldn't know/learn how to do that.

Then if I want to use the computer I would just have to shut down the Xsession or whatever is running and I could start up what I need from the commandline maybe.

The most important is that it just starts up in fullscreen and no login prompt.

---

### Post by kasperbs on 2007-07-20
Also if you  got any suggestions for a lightweight musicplayer, with a nice an easy interface for browsing music. Like rhythmbox, not vlc as someone suggsted earlier..

---

### Post by ADT on 2007-07-21
It sounds like you are looking for some sort of basic media centred type distro with browsing capabilities.

Heres a list of media oriented distros on wikipedia:
[http://en.wikipedia.org/wiki/List_of_Linux_distributions#Media_Oriented]("http://en.wikipedia.org/wiki/List_of_Linux_distributions#Media_Oriented")

You could also install ubuntu server edition and customise your system:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

After installing the server edition you would have to setup your network card through the commandline if you don't use DHCP.

You would need to uncomment the universe and multiverse repositories for aptitude in /etc/apt/sources or something like that.

You would then need to install xorg (the x windows package), a window manager such as fluxbox, icewm, etc. On a music player package like xmms,  Rhythmbox, etc.

You would then need to setup a file called .xinitrc that would start the window manager when you type "startx" in commandline.

Speaking of logging in, as far as I know, you must have a user account to login to linux. i.e you turn on the computer and in server edition a prompt will appear on screen asking for username and password.

I dont think you can automatically just login at startup (system isnt design to work that way). Any way all your dad or his wife would need is to be shown is how to type in their username and password at the prompt.

You could install gdm, a graphical display manager that has a GUI for you to log in and it starts the window manager automatically. You do not need to install the whole gnome desktop environment in order to use the gdm.

A slim system like this would probably take 20 to 40 seconds to startup.

There is a lot more to needed to know to set it up though but if you take it a step at a time and ask for help on the forum you should succeed.

---

