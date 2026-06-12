---
title: "trackpad, permissions, newbie frustrations"
date: 2007-06-13
forum: Apple PPC Users
---

### Post by mysweetisrael on 2007-06-13
hardware = iBook G4
Ubuntu = Feisty Fawn

The tap feature on the trackpad is driving me nuts.  I tried to change it by doing "trackpad notap" in Terminal.  Then I got:

opening /dev/adb: Permission denied

I loaded Ubuntu this morning but I've been reading misc FAQ, tutorials, etc. all day and I think I got the permissions right but I keep getting:

no trackpad !

How can I fix this?

Thanks,
msi.

---

### Post by Auria on 2007-06-13
when a command requires more permissions, put 'sudo' in front of it. it will then ask for your admin password

tutroials do not include it as sudo makes you all powerful (and possibly harmful) therefore it is thought good practise you decide yourself to add it and not just paste it

---

### Post by mysweetisrael on 2007-06-13
Thanks for the fast response.

Unfortunately, sudo doesn't help me.  I still get "no trackpad !"

Edit:  When I type just "trackpad", I get: "usage: trackpad notap|tap|drag|lock|show".  When I add one of those commands I get the no permission deal.  I don't get the permissions message when I use "sudo" but it still doesn't allow me to select "tap" or "notap".

---

### Post by Auria on 2007-06-13
> **mysweetisrael said:**
>  I don't get the permissions message when I use "sudo" but it still doesn't allow me to select "tap" or "notap".

If you don't get the error message, what sign do you get that tells you it does not allow it?

---

### Post by mysweetisrael on 2007-06-14
It says "no trackpad !" and nothing happens.

---

### Post by mysweetisrael on 2007-06-14
**solved**

After a day's worth of research I found an answer.  I went into *xorg.conf*, went to the "synaptics" section and added:

> Option  "MaxTapTime"  "0"

Sweet.

My next mission: to adjust the trackpad's sensitivity so the window doesn't dance when I'm typing because my thumbs get too close to and/or touch the trackpad. 

Peace,
msi.

---

