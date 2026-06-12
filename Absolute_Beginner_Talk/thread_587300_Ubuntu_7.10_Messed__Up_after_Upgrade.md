---
title: "Ubuntu 7.10 Messed  Up after Upgrade"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-10-22
In oder to get my internet working, i installed Ubuntu 7.04 and installed Envy to get my ATI Graphic Driver.

After i got my internet working, using the Update Manager, i Upgraed to 7.10 and finally managed to get internet working on Gutsy.

But the graphic interface was messed up, when evr i mouse over, everything was pixelated in rainbow colors and so on.

So, i Uninstalled Envy and also disabled ATI Driver in restricted driver manager. It asked me to reboot the machine so i did.

After the reboot, the Ubuntu only starts in command line mode, the graphical interface is lost...:confused:

How do I repair this?

---

### Post by stijngysemans on 2007-10-22
You'll need do dive into some command line tools.
you should change your xorg.conf config file and change your drive to something more usefull. maybe you can try vesa.

If this sound strange for you, don't panic. We can explain this better if you want.

---

### Post by n3tfury on 2007-10-22
take a look here:

[http://ubuntuforums.org/archive/index.php/t-399778.html](http://ubuntuforums.org/archive/index.php/t-399778.html)

---

### Post by Pumalite on 2007-10-22
At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by latheesan on 2007-10-22
Omg.. fast reply. Thanks allot guys.

What is 'vesa' ??? And if i start using that, will it finlly let me run some desktop effects?

---

### Post by latheesan on 2007-10-22
well this seems to have fixed the problem, however, the GUI is kinda fuzzy and "streched" and i still cant turn on the desktop effects to atleast "normal" :(

---

### Post by Pumalite on 2007-10-22
You can now use Restricted Drivers Manager.

---

### Post by latheesan on 2007-10-22
lol, screwed up the screen again big time, i got fedup with it and wiped the hd and re-installed Gutzy

Loving it now, im not gonna bother installing any drivers, the way it works now is perfect.

---

