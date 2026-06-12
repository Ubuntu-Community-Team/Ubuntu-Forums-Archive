---
title: "getting startup text AFTER login prompt"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by fhqwhgad on 2007-12-21
When i start ubuntu tons of text scrolls by when it loads various things. This is all fine, but eventually it should end with my login prompt.
The problem is, once it echoes the login prompt it doesn't stop echoing other stuff.
I still get text saying "Starting kernel log daemon...
Starting bluetooth services"
and alot more.

Can i fix this somehow? It looks really stupid that the login prompt isn't the last thing on the monitor.

Also, i cannot seem to shutdown.
When i do a sudo shutdown now it just ends up saying:
 * Will now switch to single-user mode
init: rc1 main process (5314) killed by TERM signal.

As a side note (i guess it might have something to do with these problems) i did not install the server version. I installed the desktop ubuntu and later disabled GDM in startup with sysv-rc-conf.

---

### Post by philinux on 2007-12-21
> **fhqwhgad said:**
> 
As a side note (i guess it might have something to do with these problems) i did not install the server version. I installed the desktop ubuntu and later disabled GDM in startup with sysv-rc-conf.

Maybe enable gdm then?

---

### Post by fhqwhgad on 2007-12-21
> **philinux said:**
> Maybe enable gdm then?

No, i still want it to start without GDM. I want to start in console mode but be able to startx if i need to.

---

### Post by philinux on 2007-12-21
Have you got 

quiet 

as part of the kernel entry in grub?

---

### Post by fhqwhgad on 2007-12-21
> **philinux said:**
> Have you got 

quiet 

as part of the kernel entry in grub?

Yes i do. I deleted splash (for some reason it seemed to cause issues when switching to 1024x768) but i left quiet in.

---

### Post by fhqwhgad on 2007-12-23
Bump.
Noone can help me with this?
I tried installing the server version and it does the same. After it prompts me with login it still keeps loading modules.

---

### Post by stuff1 on 2007-12-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the same problem this morning on a fresh install of a command line Kubuntu Gutsy setup.

I found this: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/65230")

Please see that page for full details. Just to let you know this is the workaround that worked for me: > edit /etc/event.d/tty1 and replace:

  start on runlevel 2

with:

  start on stopped rc2

---

