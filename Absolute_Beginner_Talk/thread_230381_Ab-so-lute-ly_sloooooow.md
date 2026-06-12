---
title: "Ab-so-lute-ly sloooooow"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by amugofcoffee on 2006-08-05
Is there anyway to speed up Ubuntu 5.10 on my slow computer with a Pentium II and 64 megs of RAM? It takes 5 minutes to start up the entire system.

---

### Post by Tomosaur on 2006-08-05
Unfortunately, Ubuntu's minimum reccomendation is, I think, 128mb RAM. You may want to try Xubuntu, or the Ubuntu server installation (which has no GUI).

---

### Post by Jagot on 2006-08-05
You could download BUM or something to stop non essential services booting, but really I think you should be looking at lighter weight desktop environments/window managers:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by taurus on 2006-08-05
Yes, go with the server version but install fluxbox as your window manager then...

---

### Post by Jagot on 2006-08-05
And here's a guide to setting up Fluxbox:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

### Post by sguart on 2006-08-05
> **amugofcoffee said:**
> Is there anyway to speed up Ubuntu 5.10 on my slow computer with a Pentium II and 64 megs of RAM? It takes 5 minutes to start up the entire system.

yes, throw a stick of 256mb sdram at it.
p2 350, 320meg ram, nvidia geforce4 ti4200 = ubuntu 6.06 LTS + xgl + compiz

however, this is a spare machine used to play around with ubuntu, ie performance is not critical.

good luck,
sg

---

### Post by amugofcoffee on 2006-08-05
Never mind. I downloaded XFCE and it's pretty speedy. But how do I get SCIM to work (on XFCE)?

---

### Post by OU812 on 2006-08-07
Open your package manager and do a search for scim. Depending on the repos you have enabled, you could get a lot of hits.

john

---

### Post by amugofcoffee on 2006-08-08
OK, now one last question:

XFCE has Firefox set up as the default browser. Now I want to set Galeon up as the default browser. I have installed it by executing: ```
sudo apt-get install galeon galeon-common
```. However, Galeon does not show up in the menu, and XFCE still launches Firefox when I select the Internet icon. How can I make the icon run Galeon?

---

