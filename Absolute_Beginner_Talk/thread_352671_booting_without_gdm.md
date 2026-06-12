---
title: "booting without gdm?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by ac251404 on 2007-02-03
I am running a home file server which I generally maintain through ssh. I would like to make it so that gdm doesnt run at bootup in order to save on RAM useage. However, I would like gdm to still be available to run via '/etc/init.d/gdm start' in case I need to hook up a monitor and do something using the desktop. I read a few ways to stop programs starting up but they all had to do with removing them from /etc/init.d/ is there another way?

thanks

---

### Post by bodhi.zazen on 2007-02-03
Linux is case sensitive.

Thus, rather then delete the start script, rename it.

Change it form Sxxgdm to sxxgdm (Large S to small s)

I do not recall the number represented by xx ..

You can start gdm with :```
sudo gdm
```At any time ;)

---

### Post by steve.horsley on 2007-02-03
Best is to rename /etc/rc2.d/S13gdm to s13gdm. 
**sudo mv /etc/rc2.d/S13gdm sudo mv /etc/rc2.d/s13gdm**

As bodhi says, this just changes the case so it's not recognised and started, but it stays as a reminder so you can just rename it to fix it again.

You can still start and stop gdm by hand with 
/etc/init.d/gdm start (or stop)

---

### Post by Rab22 on 2007-02-03
I would say, customize a runlevel and then make that the default runlevel.

That way, you know exactly what is booting each time. If you ever need GDM, you can still start it. 

Also, a customized runlevel gives you the advantage of going from a 'desktop' to a 'server' with simply changing one setting.

That's just me though -- the other method would work just as easily.

---

### Post by priboy on 2007-02-05
> **Rab22 said:**
> I would say, customize a runlevel and then make that the default runlevel.

That way, you know exactly what is booting each time. If you ever need GDM, you can still start it. 

Also, a customized runlevel gives you the advantage of going from a 'desktop' to a 'server' with simply changing one setting.

That's just me though -- the other method would work just as easily.

so...how to change the default runlevel?

---

### Post by Ben Sprinkle on 2007-02-05
I forget exactly, but you edit a file in /etc, might be in /rc.d?

---

### Post by bodhi.zazen on 2007-02-05
> **Ben Sprinkle said:**
> I forget exactly, but you edit a file in /etc, might be in /rc.d?

set the default run level in either grub or etc/inittab

For grub, add the boot level at the end of the kernel line, for example to set run level 3:

> kernel /boot/vmlinuz-xyz root=/dev/hdxy ro quiet splash [color=red]**3[/color]**

Again to set the defalut level to 3 (in inittab):
> id:[color=red]**3[/color]**:initdefault:

---

### Post by Ben Sprinkle on 2007-02-06
Slackware one is in /etc/rc.d is why I thought that. :P

---

### Post by bodhi.zazen on 2007-02-06
> **Ben Sprinkle said:**
> Slackware one is in /etc/rc.d is why I thought that. :P

Slackware is not the only one to use rc.d ;)

This is one area on Linux I wish there was a little more standardization - file system structure and CLI configuration tools, for example networking.

---

