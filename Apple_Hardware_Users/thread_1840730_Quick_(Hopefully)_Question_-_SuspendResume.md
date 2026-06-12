---
title: "Quick (Hopefully) Question - Suspend/Resume"
date: 2011-09-08
forum: Apple Hardware Users
---

### Post by svtguy88 on 2011-09-08
Is suspend/resume supported on PowerPC?  I just spent a few hours with Google, and I'm pretty much right where I started.

Clicking "Suspend" on the logout screen does nothing (returns to the desktop).  I get nothing as well when issuing either of the following:

```
root@powermac-debian:/home/pat# pm-suspend
root@powermac-debian:/home/pat# s2ram

```

I guess I should mention my machine is a G4 with an nVidia card, running XFCE with the nv driver.  I read a lot of mailing lists and forum posts, and everything seems to say the ATI cards are more well supported, but I can always hope, right...?

---

### Post by linuxopjemac on 2011-09-08
Macs with nVidia cards will not suspend under Linux, there is no support as far as I know.

---

### Post by rsavage on 2011-09-08
I noticed with recent kernels that it isn't reporting that suspend is available (I have a radeon card).  That I presumed was why the suspend buttons weren't working although I never looked into it with any effort.  I was able to suspend through installing powerprefs (I don't think it installs itself on the menu so you may have to invoke it from the terminal).  For example, setting it to suspend when you close the lid (you may  have to adjust your gnome power preferences settings so they don't  clash).  

It's always worth giving it a go.  It may work with the nouveau driver and a recent kernel!  Install xubuntu 11.04!

---

### Post by svtguy88 on 2011-09-08
rsavage - I assume you have an ATI card?

I could have sworn that about a two years ago, I did an install on my Powerbook (Debian Lenny, I think it was), and for some reason I remember suspend working (at least partially...maybe it slept, but didn't resume the display.  I don't really remember).  

Not having a working suspend/resume is really going to be a problem for me, as I'm trying to set my Powermac up as a server (and router) that would wake-on-lan...

---

