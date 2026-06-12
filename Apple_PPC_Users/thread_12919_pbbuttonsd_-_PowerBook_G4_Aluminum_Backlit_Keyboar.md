---
title: "pbbuttonsd - PowerBook G4 Aluminum Backlit Keyboard Problem"
date: 2005-01-27
forum: Apple PPC Users
---

### Post by usr3301 on 2005-01-27
I am running Ubuntu Linux on my Powerbook (all details and specs below).  pbbuttonsd is installed and running.  My eject, volume, and brightness keys all function properly.  When I try to adjust the backlit keyboard (F8 - F10 keys), nothing happens.  When I go in a dark room, the keyboard does not light.  This functionality did work with pbbuttonsd on Yellow Dog Linux 4.  When I try to use powerprefs to modify the settings, the backlit keyboard portion is "greyed out".

I have read that pbbuttonsd needs the i2c-keywest and i2c-dev kernel modules.  i2c-keywest is compiled into the kernel.  When I modprobe i2c-dev, the module loads.  I then do a stop/start of pbbuttonsd and open powerprefs again.  This time it the backlit keyboard is no longer greyed out.  If I try to set the keys to F8 - F10, it doesn't see input.  The backlit keyboard also does not function in a dark room.

Any ideas or help would greatly be appreciated.  This is the last thing I need to get working (aside from the built-in Airport Express which I think is hopeless right now).

So far, Ubuntu is the best Linux distribution for PPC I have used; much better then Yellow Dog 3 or 4.  For the most part, everything worked out of the box, including sound.  Yellow Dog couldn't even make sound work.

OS:  Ubuntu 5.04 "Hoary Hedgehog"
Kernel:  2.6.10-2-powerpc
* All the latest packackages and updates have been applied.
Laptop Hardware:  PowerBook G4 Aluminum 15", 1.5GHz /w backlit keyboard
PBBUTTONSD Ver:  0.6.6-3

Thank you so much!

---

### Post by adamw on 2005-01-29
Wow, it looks like you're a step ahead of me.  I will take a stab at the backlit kb steps and see what I end up with.  You haven't set up vpn by any chance, have you?

---

### Post by adamw on 2005-02-03
You should have an /etc/pbbuttons/pbbuttonsd.conf file.  Inside that file there is a:

#KBD_Brightness     = 0

Change it to:

KBD_Brightness     = 10

hth,
Adam

---

### Post by usr3301 on 2005-02-13
Changing the initial backlit keyboard value to 10 did not work.  The keyboard still did not illuminate.  The keyboard brightness keys also have no effect.  Any other ideas?  Thanks!

---

### Post by BeTa on 2005-03-01
[QUOTE=usr3301]Changing the initial backlit keyboard value to 10 did not work.  The keyboard still did not illuminate.  The keyboard brightness keys also have no effect.  Any other ideas?  Thanks![/QUOTE]

I get the same thing here... I'm running the warty release w/o any significant backport. I'm sad because I'd love to see this feature on my GNU/Linux :c(.

---

### Post by barrack on 2006-07-11
> **usr3301 said:**
> I am running Ubuntu Linux on my Powerbook (all details and specs below).  pbbuttonsd is installed and running.  My eject, volume, and brightness keys all function properly.  When I try to adjust the backlit keyboard (F8 - F10 keys), nothing happens.  When I go in a dark room, the keyboard does not light.  This functionality did work with pbbuttonsd on Yellow Dog Linux 4.  When I try to use powerprefs to modify the settings, the backlit keyboard portion is "greyed out".

I have read that pbbuttonsd needs the i2c-keywest and i2c-dev kernel modules.  i2c-keywest is compiled into the kernel.  When I modprobe i2c-dev, the module loads.  I then do a stop/start of pbbuttonsd and open powerprefs again.  This time it the backlit keyboard is no longer greyed out.  If I try to set the keys to F8 - F10, it doesn't see input.  The backlit keyboard also does not function in a dark room.

Any ideas or help would greatly be appreciated.  This is the last thing I need to get working (aside from the built-in Airport Express which I think is hopeless right now).

So far, Ubuntu is the best Linux distribution for PPC I have used; much better then Yellow Dog 3 or 4.  For the most part, everything worked out of the box, including sound.  Yellow Dog couldn't even make sound work.

OS:  Ubuntu 5.04 "Hoary Hedgehog"
Kernel:  2.6.10-2-powerpc
* All the latest packackages and updates have been applied.
Laptop Hardware:  PowerBook G4 Aluminum 15", 1.5GHz /w backlit keyboard
PBBUTTONSD Ver:  0.6.6-3

Thank you so much!


How do I load a kernel? I am trying to do the same thing as you all, but am very new to this. I installed pbbuttonsd and looked about in powerprefs, but got the same greyed out thing. I also read that installing this kernel and rebooting would do the trick.

---

### Post by ibbumpin on 2006-11-02
To load the kernel go to your /boot directory and point your vmlinux.img and initrd.img to your newest vmlinux installations.  Then add the i2c-dev to your /etc/modules file and your keyboard lighting should work.  Your linux kernels can be compiled from source or updated through apt-get or your gui package update application.

---

### Post by ibbumpin on 2007-11-02
for Ubuntu 7.10 if your keyboard buttons don't work try:

modprobe i2c-dev && pssbuttonsd

---

