---
title: "Sound Controller On Edgy"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by emrextreme on 2007-04-13
Accidentally removed the sound controller icon  on Kubuntu Edgy and now i can't turn the sound up and down. Which app. should i add to panel make it work?
Tnx.

---

### Post by atihimself on 2007-04-13
Did you removed it from the bar at the upper left corner, or you totally removed it
If you just lost the icon, then right click on the upper or lower bar and click  add... well I'm at work can't make it step-by-step (this add... something with green + next to it) and from there you should find volume controller

---

### Post by emrextreme on 2007-04-13
> **atihimself said:**
> Did you removed it from the bar at the upper left corner, or you totally removed it
If you just lost the icon, then right click on the upper or lower bar and click  add... well I'm at work can't make it step-by-step (this add... something with green + next to it) and from there you should find volume controller

No, just removed the icon. But there is no controller app. in the "add apps. menu". (No green stuff or else) 
Appreciate for any help.
Tnx.

---

### Post by caffienefree on 2007-04-13
Go to system>Preferences>Sessions. Is there an an entry called volume manager, and is in enabled? If it is not enabled, click the check mark and reboot. If the entry is not there, click new, and add **gnome-volume-manager --sm-disable**, then reboot.

---

### Post by emrextreme on 2007-04-13
> **caffienefree said:**
> Go to system>Preferences>Sessions. Is there an an entry called volume manager, and is in enabled? If it is not enabled, click the check mark and reboot. If the entry is not there, click new, and add **gnome-volume-manager --sm-disable**, then reboot.

Sorry for misunderstanding. My bad!
I'm using Ubuntu with KDE-Core. (a.k.a. Kubuntu) and there is no sessions section neither gnome-volume-manager.
What is the peer app. of the gnome-volume-manager on Kubuntu?

---

### Post by emrextreme on 2007-04-13
Sorry, bump.

---

### Post by caffienefree on 2007-04-13
[http://lists.kde.org/?l=kde-linux&m=116657092501055&w=2](http://lists.kde.org/?l=kde-linux&m=116657092501055&w=2)

---

### Post by emrextreme on 2007-04-14
> **caffienefree said:**
> [http://lists.kde.org/?l=kde-linux&m=116657092501055&w=2](http://lists.kde.org/?l=kde-linux&m=116657092501055&w=2)

Tnx a lot. Bullseye! Problem solved.

---

