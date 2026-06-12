---
title: "uninstall error nvidia restricted driver..."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-12
hi,

i uninstalled nvidia restricted driver and i cannot use Ubuntu anymore...i just get a white screen...

please help i destroyed Ubuntu yesterday and had to re-install it...

---

### Post by undertakingyou on 2007-08-12
Try starting in recovery mode and run ```
 sudo apt-get install nvidia-glx-new
```  That should reinstall the driver.  for older cards replace "new" with "legacy" in the above line.

---

### Post by SOULRiDER on 2007-08-12
Everything locks up ebcause Xorg tries to use a driver that is not present anymore. You can either reinstall the driver like undertakingyou or you can edit the xorg configuration to use the nv driver instead of the nvidia driver.

IMHO, id choose to install ht epropietary driver.

---

### Post by Hopeless on 2007-08-12
Hi,

Thanks for the info i will install again like you said.....

> Try starting in recovery mode and run

But how can i do that?

---

### Post by undertakingyou on 2007-08-12
when the computer start it should say something like "loading grub".  Get into the grub menu by hitting escape and then select the entry that says "recovery mode".  It will boot to a command line and then you can run that command.  After that run ```
 sudo gdm restart
``` and all *should* be well.

---

### Post by Hopeless on 2007-08-12
Got it!!!!

A **[SIZE="7"]BIG[/SIZE]** Thank-You !!! :KS

---

### Post by Zer0Nin3r on 2007-08-16
> **undertakingyou said:**
> when the computer start it should say something like "loading grub".  Get into the grub menu by hitting escape and then select the entry that says "recovery mode".  It will boot to a command line and then you can run that command.  After that run ```
 sudo gdm restart
``` and all *should* be well.

Another method that is currently working for me (because I have the same problem) is just to boot normally

 perform a ctrl+alt+backspace to get back to the login screen

click on 'Options'

select "Sessions"

select "Failsafe Gnome"

and from there you can operate normally.  Pull up a terminal and take care of whatever business you have.

***Update***
Nope.  The method I mentioned only worked once.  Even if I boot and select a safe session, once Beryl boots up I'm toast.  Still trying to figure it out.

---

