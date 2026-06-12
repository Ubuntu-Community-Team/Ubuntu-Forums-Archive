---
title: "Misc questions about KDE..."
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Anessen on 2007-05-06
Hey, I'm a Kubuntu user and I just have a few questions about where things are in KDE as opposed to Gnome. 

On my laptop, I have chosen to use KPowerSave instead of the default tool that appears on KDE automatically. How can I disable the default power manager app?

Also, how  can I disable the session restore system in KDE? It's a nice idea, but it does cause problems with some programs, and I would rather just start up what I need each time.

Finally, not related to KDE, but what ATI driver should I be using? I have an ATI X200 integrated chipset. At the moment, my xorg.conf says I am using the "ati" driver.

---

### Post by benerivo on 2007-05-06
The session manager options are in the Control Centre, in either Settings>Control Center, or just System Settings from the KDE start menu.

---

### Post by argux on 2007-05-06
About the ATI graphics card, I've got the same graphics card on my laptop, and the driver provided in the repositories made my computer crash on shutdown, so I tried the official ATI drivers and I don't have that problem anymore. I used this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), using the Install from ATI/ Feisty option.

Of course, your mileage may vary, but in any case, if you have any problems, you can just change the driver in xorg.conf from fglrx back to ati, and restart the server.

---

