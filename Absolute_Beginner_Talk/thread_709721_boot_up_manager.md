---
title: "boot up manager"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-02-27
so my boot up time has gotten very slow lately, I haven't re-installed Ubuntu in a LONG time (very different from the 6 monthly windows install!), but I recently installed Boot up manager, and saw that there are numerous programs that I don't recognise (and so am to scared to shut off), if anyone could provide some help with this, it would be greatly appreciated!

---

### Post by chris.a.barker on 2008-02-27
Perhaps the best start would be for you to take a screenshot and show us what programs are running. This way we can make the call on what you can stop.

---

### Post by abhiroopb on 2008-02-27
screenshot of what exactly? top? the bootup manager?

---

### Post by philinux on 2008-02-27
Either click the link below for known bugs, slow boot is one. Or install and run startupmanager.

---

### Post by chris.a.barker on 2008-02-27
The boot manager.

---

### Post by abhiroopb on 2008-02-27
Screenshots (3)

---

### Post by abhiroopb on 2008-02-27
Also just after GRUB times out I get a funny few lines of text (something to do PCI:... - basically a lot of writing), and then it says Starting Up.

This bit usually takes a while.

---

### Post by Vadi on 2008-02-27
It looks fine as it is. In fact you disabled a bit too many things I'd say (apport is useful).

The delay in bootup could be causing to something failing during bootup.. there are boot logs you can view somewhere, but I don't know where. Try system - administration - system log.

---

### Post by abhiroopb on 2008-02-27
Thanks

It isn't really that slow, but was wondering if there were any other things I could disable.

A few things:

Just after grub I get the following:

> 
Starting up...
(some text): PCI: Cannot allocate resource to region 7 of bridge....
.
.
.
.
.
Loading...


left out a few bits there but yea I don't understand this.

Next for some reason I've been getting:

> 
Internal Error:
Failed to initialise HAL!


any thoughts?

---

### Post by abhiroopb on 2008-02-27
Just to add:

- Solved the HAL error.

- Shutdown time is: 20s
- Boot-up: 45s
- Login screen (till the point I can use the comp): about 1min 10s

The time it takes from the display of the login screen to usability seems a little high. Is this a bug or is there anything I can do to change this?

---

### Post by Vadi on 2008-02-28
After you login, the stuff is being launched from system - administration - sessions.

I keep my number low, and get like a 3-5 second usability after login.

---

### Post by abhiroopb on 2008-02-28
don't u mean system-preferences-sessions? (or is that only in gutsy?) I have the following in startup:

KKBswitch (quite essential, allows me to switch between UK/US keyboard)
nm-applet
gnome-power-manager
gnome-volume-manager 
update-notifier
gworldclock

I can't image just these are slowing the speed to over a minute!

---

### Post by Vadi on 2008-02-28
Not that then I guess.

No idea, sorry.

---

### Post by abhiroopb on 2008-02-28
thanks for the help anyway!

---

