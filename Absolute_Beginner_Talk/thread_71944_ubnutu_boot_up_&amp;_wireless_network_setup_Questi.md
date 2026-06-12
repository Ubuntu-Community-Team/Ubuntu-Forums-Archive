---
title: "ubnutu boot up &amp; wireless network setup Question"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by helmethedd on 2005-10-04
1. Is it normal to see streaming lines of technical mumbo jumbo scroll up the screen during boot up? (white on black screen)

2. Is there a way to speed up the boot up process?
3. I have to put into the terminal "modprobe ndiswrapper" and then go to admin>network>wireless>activate, each time i turn on my laptop. Isn't there a better way?

---

### Post by brentoboy on 2005-10-04
[QUOTE=helmethedd]1. Is it normal to see streaming lines of technical mumbo jumbo scroll up the screen during boot up? (white on black screen)
[/QUOTE]
yeah, thats normal

---

### Post by brentoboy on 2005-10-04
[QUOTE=helmethedd]2. Is there a way to speed up the boot up process?
[/QUOTE]

I dont think so, but I bet you loose a lot of time waiting for it to configure networks that arent responding, so it might be faster after you fix your modprobe ndiswrapper dilema

---

### Post by brentoboy on 2005-10-04
[QUOTE=helmethedd]3. I have to put into the terminal "modprobe ndiswrapper" and then go to admin>network>wireless>activate, each time i turn on my laptop. Isn't there a better way?[/QUOTE]

sudo ndiswrapper -m
(I think)

then, reboot, does that help?

---

### Post by Ampersand on 2005-10-04
1) Yes. (:
There will be an option for this to take place behind a splash screen in the Breezy release.

2) You can edit what starts on startup using the Services configuration in System - Administration (I think, not in gnome at the moment). Unselecting NTP server should take a bit of time off.

---

### Post by helmethedd on 2005-10-04
I hate to sound like a ninny, but will that mess anything up?
I'd rather keep it the way it is rather than hafta try and fix something that i already don't understand. I've only had linux now fer about 3 days....

---

### Post by helmethedd on 2005-10-04
[QUOTE=Ampersand]1) Yes. (:
There will be an option for this to take place behind a splash screen in the Breezy release.
2) You can edit what starts on startup using the Services configuration in System - Administration (I think, not in gnome at the moment). Unselecting NTP server should take a bit of time off.[/QUOTE]
I'm using hoary. 
Yet if this is normal, i wont worry about it, i'd like to see it go faster tho if poss.

---

### Post by Ampersand on 2005-10-04
the ntp (network time protocol) service syncronises your clock with an online one. If it can't connect to it, then it can extend the startup time by a minute or two. I'd only recommend it if you see the line "Syncronising with ntp.ubuntulinux.org  [fail]" when you start up. Otherwise it's probably not worth it.

---

### Post by helmethedd on 2005-10-04
i have seen that! Care to walk me thru fixing that?

---

### Post by Ampersand on 2005-10-04
You should have a menu bar on one of the panels on your desktop. Go to System - Administration - Services. Enter your password when prompted, and then uncheck the box next to 'Clock synchronization service (ntpdate)' and press Ok.

---

### Post by helmethedd on 2005-10-04
i looked, alas nothing called services under admin or preferences....could it be called something else?

---

### Post by Ampersand on 2005-10-04
Is it under Applications - System tools?

If not, try running 'gksudo services-admin' from a terminal. It's possible that it was added in Breezy, though.

---

### Post by helmethedd on 2005-10-04
i didn't find it there either.
I tried the other suggestion, but if it should have responded in some noticable way, it didn't.
Was that intended to have fixed it in the background?

---

### Post by drogoh on 2005-10-04
[QUOTE=helmethedd]
3. I have to put into the terminal "modprobe ndiswrapper" and then go to admin>network>wireless>activate, each time i turn on my laptop. Isn't there a better way?[/QUOTE]

Yep!  Open /etc/modules in your favorite text editor (through sudo or gksudo to gain root access rights, of course) and just add ndiswrapper on its own line at the very bottom.

Once you have saved this file, Ubuntu will automatically load the ndiswrapper module, if it's available, when it is booting.

---

### Post by drogoh on 2005-10-04
[QUOTE=Ampersand]the ntp (network time protocol) service syncronises your clock with an online one. If it can't connect to it, then it can extend the startup time by a minute or two. I'd only recommend it if you see the line "Syncronising with ntp.ubuntulinux.org  [fail]" when you start up. Otherwise it's probably not worth it.[/QUOTE]

I've never seen ntpdate hang the boot process unless name resolution is acting up.  If the network is not available, it should bail instantly. (unless you're querying your router and the router in turn is sending a request out when the network is down)

---

