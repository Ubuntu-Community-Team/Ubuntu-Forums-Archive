---
title: "Boot Up Graphics Problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by tdashroy on 2008-01-27
Hi I am pretty new to Ubuntu and I updated recently to 7.10, but whenever I boot up now It always says that I am running in low graphics mode and it gives me the option to configure to my graphics card.  I have an Intel 965 graphics card and I have heard it is blacklisted, which I have no idea what means, but if anybody could help me it would be greatly appreciated.

---

### Post by syn` on 2008-01-27
I think the blacklist is talking about the card being blacklisted by Compiz. 

However, I found this in a similar thread:

> I've got a 965 Chipset, and I've also had problems with graphics (screen going blank, error messages). I read on the Intel site that the distros may only have the drivers through the 945 model. Apparently, the only solution is to wait for Hardy Heron or wait for Ubuntu to send out a driver update.

So my guess would be check the Intel site and see what they have to say about it or just google something like "Intel 965 Problems" -- you're bound to come across something more helpful than I can personally tell you.

---

### Post by tdashroy on 2008-01-27
okay I will try searching on google, thanks for the help, I figured I would try here first before searching since you guys have been able to solve all of my other problems.

---

### Post by Majorix on 2008-01-27
Try running in recovery mode (it is an option at the bootup) and run this command when you get to the prompt:
```
dpkg-reconfigure -phigh xserver-xorg
#After the configuration run this:
reboot
```

Hope it was helpful.

---

### Post by AnonCat on 2008-01-27
You can check your blacklist file by typing the following in the terminal:

sudo gedit /etc/modprobe.d/blacklist

If it was blacklisted though it shouldn't work at all even in low graphics mode.  You could change your xorg.conf file to use the vesa driver which should give you a more tolerable GUI at least.

---

### Post by Majorix on 2008-01-27
You shouldn't change the xorg.conf file by hand. The command I gave will automatically adjust it. You just have to select vesa for the driver if you have to.

---

### Post by tdashroy on 2008-01-27
Thanks Majorix, when I did that it did not come up with the running in low graphics mode so I guess it is fixed.  Do you know when I will be able to use my actual driver for the Intel 965?

---

