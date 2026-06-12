---
title: "How do I make Gaim start automatically on system startup?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by ddh33 on 2007-02-01
I've tried to add it to the list of startup services under Admin>Services but it's not there. My friends often complain they don't see me online anymore. lol

Thanks :)

---

### Post by ThrobbingBrain66 on 2007-02-01
> **ddh33 said:**
> I've tried to add it to the list of startup services under Admin>Services but it's not there. My friends often complain they don't see me online anymore. lol

Thanks :)

The correct place to add it is System>Preferences>Sessions

Then just go to the Startup Programs tab and add gaim

---

### Post by catlee on 2007-02-01
It's very simple- System -> Preferences -> Session -> Start up (tab) and then add Gaim. 

Good Luck!

---

### Post by ddh33 on 2007-02-03
Thanks for the heads-up. Did as told. 

However it's not working...the icon doesn't show up in the notification area. When I go into Session to see the list of currently running programs, Gaim isn't in there either. It is indeed in "Startup programs."

What is wrong? :confused:

---

### Post by dbbolton on 2007-02-03
you wouldnt happen to be using a failsafe gnome session, would you ?
=====

highly undesirable idea:

```
gksudo gedit /usr/bin/startgaim.sh
```paste this:

```
#!/bin/sh
 gaim
 sleep 4
 exec gnome-session
```save and exit. then:

```
sudo chmod a+x /usr/bin/startgaim.sh
```
now make a new session:

```
gksudo gedit /usr/share/xsessions/Gaim.desktop
```add: 
```
[Desktop Entry]
Encoding=UTF-8
Name= ***Whatever you want to call it ****
Exec=/usr/bin/startgaim.sh
Icon=
Type=Application
```
when you login, choose Options in the lower left, and pick Sessions, and select the one you just made. if the new session doesnt work, restart X with ctrl+alt+backspace to get back to the login screen.

note: this is a pretty ridiculous idea.

---

### Post by freeflyer57 on 2007-03-04
did it work? Are you sure that the command is right? "gaim"

---

