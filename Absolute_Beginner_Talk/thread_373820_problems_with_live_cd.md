---
title: "problems with live cd"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by doppely on 2007-03-01
Hi I tried testing the latest stable ubuntu version on my laptop, but the screen did weird things its not supposed to. The boot menu showed up just fine, but when I hit the start/install ubuntu button. It happened. After loading some things the screen faded to black, then every other line turned white and you could tell where the pressure points on the screen are. Sorry for this vague description, it looks like a graphic card problem to me.
I have a Compaq Presario V6101US Notebook PC.

Can anyone help? I already tried the safe graphics setting. 
Thanks

- Joshua.

---

### Post by luke411 on 2007-03-01
Did you burn the cd slowly or just use the default settings on your cd software. If you burn the live cd too quickly, it can cause it to not work.

---

### Post by nudnik on 2007-03-01
> **doppely said:**
> Hi I tried testing the latest stable ubuntu version on my laptop, but the screen did weird things its not supposed to. The boot menu showed up just fine, but when I hit the start/install ubuntu button. It happened. After loading some things the screen faded to black, then every other line turned white and you could tell where the pressure points on the screen are. Sorry for this vague description, it looks like a graphic card problem to me.
I have a Compaq Presario V6101US Notebook PC.

Can anyone help? I already tried the safe graphics setting. 
Thanks

- Joshua.

Linux hates Presario graphical configurations, especially old ones. You will have to modify xorg.

If you wish to experiment with this, install to an unused (read non-critical spare) disk and try the fun and games listed below.  

If and I do mean if, you can access the command line interface (hit ctrl-alt-F1) you can attempt the following:

sudo -s
(type password)

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xorg-conf

Choose your resolution, etc. and once back to the CLI type the following:

sudo /etc/init.d/gdm start

If you get Wacky Screen again, you will need more expert help. One of the Ubunti will have to instruct you how to manually edit xorg from the CLI. That might work. Maybe. We will sacrifice a goat on your behalf just in case. See mascot below.

---

