---
title: "Booting to Brown Screen"
date: 2006-10-03
forum: Apple PPC Users
---

### Post by munchbach on 2006-10-03
Well, foolishly I changed my auto-login option to "enable" whenever I boot into Ubuntu now on my PowerBook GDM fires up but hangs at the brown screen where the login manager whould usually fire up.  I'm not really familiar with Ubuntu is there any way to correct this?  In other versions of linux i would have typed "linux 1" at startup to start to the command prompt and go from there but that does not seem to work.

Any help would be greatly appreciated.

Cheers,
Andrew

---

### Post by linear on 2006-10-03
Try editing /etc/X11/gdm/gdm.conf.

There is an "AutomaticLoginEnable" key there.

---

### Post by munchbach on 2006-10-03
> **linear said:**
> Try editing /etc/X11/gdm/gdm.conf.

There is an "AutomaticLoginEnable" key there.

Thank you for the response.  How do I boot without GDM firing up automatically though?  That appears to be where the problem is.

Thanks again for your help.

---

### Post by devils_casper on 2006-10-03
Hi !

boot up through Ubuntu CD and edit /etc/X11/gdm/gdm.conf.



casper

---

### Post by linear on 2006-10-03
> **munchbach said:**
> How do I boot without GDM firing up automatically though?

That's a bit of a problem on a Mac, as there's no boot option to go directly to a command prompt.

Try ctrl-alt-F1 when you get to the brown screen (or before); that's supposed to drop you to a shell. Try it a few times if it doesn't work at first.

---

### Post by applemacmad on 2006-10-04
BSOD - Brown Screen of Death ;)

---

### Post by munchbach on 2006-10-04
Yeah, ended up hosing the system and starting from scratch.  Oh well, I'm a compulsive backer'uper so I didn't loose anything.

Cheers,
Andrew

---

