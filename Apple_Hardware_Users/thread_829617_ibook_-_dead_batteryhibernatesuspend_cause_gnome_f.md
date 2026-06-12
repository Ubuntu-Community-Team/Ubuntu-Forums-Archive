---
title: "ibook - dead battery/hibernate/suspend cause gnome failure on reboot"
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by influx.ca on 2008-06-15
I've had 2 instances where the iBook has run out of juice. I had the controls set to "shutdown" when this happens. There were also a few times when it went into hibernate mode. However when I rebooted, everything went fine until I got to the desktop. The desktop picture would appear, but that was it. No menus sidebars or anything - GNOME would not load (I assume) I tried booting GNOME in safe mode and the same thing happened.

I ended up re-installing. and for now, I am just watching the battery levels and shutting down manually every time.

Does anyone know why this could be happening, or how I could prevent it from happening again?

I'd even be happy with knowing how to fix it without having to re-install.

---

### Post by stream303 on 2008-06-16
Power management always seems to be tricky.  For now, i'd disable the hibernate feature until a fix or update comes along.  I could never get it to work right with my nvidia-driven ibook, but there might be hope for ati video models..

Which ibook are you running, and which version of Ubuntu?
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

---

### Post by influx.ca on 2008-06-16
Thanks for the reply. [CLICK ME]("http://www.everymac.com/systems/apple/ibook/stats/ibook_g4_1.33_12.html") <-- the iBook I am using. I am running Ubuntu 8.04

When you say disable Hibernate, do you mean just deselect it in preferences, or do something in Terminal to disable it? If so, how would you do that?

Also, is there a script or something I could use that would automatically engage Shutdown when the battery level gets to a certain percentage?

---

### Post by stream303 on 2008-06-16
You may want to see this nice addition to the powerpc known faq:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-5cdcb8ed2e1c81fb49e0f22782bf67c86d911ca7](https://wiki.ubuntu.com/PowerPCKnownIssues#head-5cdcb8ed2e1c81fb49e0f22782bf67c86d911ca7)

I'm not sure if pbbuttonsd will work on your machine - but the info here looks helpful.

---

