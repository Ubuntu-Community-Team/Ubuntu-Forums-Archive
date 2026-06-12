---
title: "Ubuntu Server on a Mac Mini boot problem"
date: 2007-07-27
forum: Apple Intel Users
---

### Post by tjockis on 2007-07-27
Hey everybody!

I have a mac Mini running Ubuntu (LAMP) Server 7.04. Everything works great and I am somewhat in love with the setup :)

The only problem is, I need to be able to do some amount of remote administration.. And as it is now, linux won't boot unless I plug in a keyboard and a screen. If I want to reboot it, i have to connect them physically and then disconnect them when everything has loaded. Kinda frustrating... I have listened to the hard dive both when I have connected ant no connected the peripherals It seems as if GRUB does its thing, but then i freezes on the startup. And the mini gets warm with wizzing fans. Requires me to force shutdown the box.


Any ideas?

Cheers!

---

### Post by cyberdork33 on 2007-07-27
I can't help with the keyboard problem, but the Display problem is well known.

You can get somethign like this:
[http://www.drbott.com/prod/db.lasso?code=0153-GHDD](http://www.drbott.com/prod/db.lasso?code=0153-GHDD)

or you can do something like this:
[http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy](http://blackfriarsinc.com/blog/2007/04/how-to-keep-headless-mac-mini-happy)

As far as I have seen that should be all you need to get it to boot.

---

### Post by pspcz on 2007-07-27
we posted re this same issue yesterday and were helped out by cyberdork as well

keyboard is not needed, i am waiting for the dongle from dr bott to see if that does the trick for the monitor

btw,this is not an issue i am told if you run os x server on the intel mini, we have been running os x server on a ppc mini for a few years and it is definately not an issue with that setup

does anyone have any info on how to set up an automatic restart on 7.0.4 after a power failure?


Pz

---

### Post by cyberdork33 on 2007-07-27
> **pspcz said:**
> btw,this is not an issue i am told if you run os x server on the intel mini, we have been running os x server on a ppc mini for a few years and it is definately not an issue with that setup

I think there are some minor issues, like you have to set a bluetooth option correctly, otherwise it will complain on boot about a missing keyboard. Also, I have heard that remote desktop acts funny without a monitor connected. This is just information I have seen online and don't know if this applies to OSX, OSX server or both.

> does anyone have any info on how to set up an automatic restart on 7.0.4 after a power failure?

On most PCs, that is a BIOS option. Since there is no BIOS on a Mac, I can't give you any leads... How would you set this in OSX?

---

### Post by pspcz on 2007-07-27
these guys seem to be all over it 

[http://www.mythic-beasts.com/support/macminicolo_howto.html]("http://www.mythic-beasts.com/support/macminicolo_howto.html")


Pz

---

