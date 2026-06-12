---
title: "vlc won't open"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by uzybear on 2008-01-21
so i click it and nothing happens; xubuntu GG on an ibm x30 thinkpad; it was working fine and now won't even open; i try to play stuff with mplayer, but it gives me a "gnome screensaver error"

---

### Post by DMK62 on 2008-01-21
There was an update to xorg last week that caused several problems including vlc not loading. Check for new updates with your update manager or run sudo apt-get update and sudo apt-get upgrade from a terminal. They released a fixed version of the xorg update last week.

hth

Dale

---

### Post by uzybear on 2008-01-21
did that and still don't work

---

### Post by DMK62 on 2008-01-22
If you start vlc from the terminal does it give you any errors ? Just type vlc in the terminal to start it.

Dale

---

### Post by uzybear on 2008-01-22
x window system error

badalloc (insufficient resources for allocation)


i got oodles of resources

512mb

---

### Post by DMK62 on 2008-01-22
Run from the terminal  Xorg -version

what does it give you for the Build Operating System: Linux Ubuntu 

Mine is Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)

Vlc is working fine with that version.

Dale

---

### Post by FuturePilot on 2008-01-22
If you installed an update for xorg make sure you log out and back in so X can restart with the new version.

---

### Post by DMK62 on 2008-01-22
FuturePilot, thanks for pointing that out that x needs to be restarted.

---

### Post by Fallenknight71 on 2008-01-22
Hello to all,
Brand new Ubuntu user as of last week.   I had this problem too and the update and upgrade worked perfect.  But only after I logged out and restarted.  So thanks to you all for the help in this.

---

