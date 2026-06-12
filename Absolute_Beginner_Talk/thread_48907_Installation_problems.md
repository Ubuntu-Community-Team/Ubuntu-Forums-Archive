---
title: "Installation problems"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by tmattisson on 2005-07-14
I'm installing ubuntu for the first time on a Dell Latitude D410 and I'm having problems with X. The automatic X configuration messes up so I only get a blank page when it starts the X server during installation. So what do I do now? It don't think the installation is complete since I haven't even been asked to enter the password for root. If I reboot I can get X running and change the root password, but I'm guessing the installation is incomplete. Are there any more installation steps when the installation starts X?

/Thomas

---

### Post by geocritter on 2005-07-14
[QUOTE=tmattisson]I'm installing ubuntu for the first time on a Dell Latitude D410 and I'm having problems with X. The automatic X configuration messes up so I only get a blank page when it starts the X server during installation. So what do I do now? It don't think the installation is complete since I haven't even been asked to enter the password for root. If I reboot I can get X running and change the root password, but I'm guessing the installation is incomplete. Are there any more installation steps when the installation starts X?

/Thomas[/QUOTE]
 Not sure why X is having trouble.  About root: there is no root set up in Ubuntu (although I think you CAN set it up if you want, just google it to find out how).  You log in as user, and "sudo" everything.  It's the only distribution that I know of that does it.  Kind of aggravating for those of us switching from other distros, but at the same time, it's starting to grow on me.  A good protection, in some ways.

Now...on X...you might try logging in normally on a terminal screen (go CTRL + ALT + F2 or F3 (one of those F key) to bring up a terminal screen, then "sudo xorgconfig"  I think it's xorgconfig, or xorgconf.  That will let you set up X; you can choose a monitor that will like your lcd screen.

I haven't done this in Ubuntu, so if anybody knows about it and I'm wrong, please please please correct me.

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=tmattisson]I'm installing ubuntu for the first time on a Dell Latitude D410 and I'm having problems with X. The automatic X configuration messes up so I only get a blank page when it starts the X server during installation. So what do I do now? It don't think the installation is complete since I haven't even been asked to enter the password for root. If I reboot I can get X running and change the root password, but I'm guessing the installation is incomplete. Are there any more installation steps when the installation starts X?

/Thomas[/QUOTE]

Sounds like:

A: A bad install

B: A bad install CD (which lead to a bad install)

The install CD is very sensitive. Much more than say....a music cd. Try reinstalling...and if you get the same problems (aka your install CD is bunk...it happens to me too) then reburn the ISO at lower speeds.

---

### Post by markg on 2005-09-15
[QUOTE=tmattisson]I'm installing ubuntu for the first time on a Dell Latitude D410 and I'm having problems with X. The automatic X configuration messes up so I only get a blank page when it starts the X server during installation. So what do I do now? It don't think the installation is complete since I haven't even been asked to enter the password for root. If I reboot I can get X running and change the root password, but I'm guessing the installation is incomplete. Are there any more installation steps when the installation starts X?

/Thomas[/QUOTE]
 I'm having the same problem with installing ubuntu on my Inspiron 1200.  No errors, it appears to install everything,but when X starts the lcd seems to sync out or fades to black.  I can push the power button and the standard text screen will appear and the system reboots.  Please help me too.....

---

