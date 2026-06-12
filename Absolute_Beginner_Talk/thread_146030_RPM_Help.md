---
title: "RPM Help"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by ddavi4 on 2006-03-17
Morning all! Totally new Ubuntu user here. I am attempting to install a driver for my sound card. I have the driver & have attempted to install from the command line with the "rpm -ivh andmyrpmfile" and I receive the following error message "bash: rpm: command not found" so I am now totally lost. I did also make sure that I logged in as SU. Any help would be greatly appreciated. Thx Doug

---

### Post by taurus on 2006-03-17
You need to convert it to .deb first before you can install it.  Do these from a terminal,
```

sudo apt-get install alien
sudo alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

---

### Post by ddavi4 on 2006-03-17
Taurus, THANKS FOR THE HELP. The instruction that you gave me worked perfectly, however I am still seeing my speaker "greyed" out & have no volume control. I am missing a step here in regards to configuration? This happens to be a Dell box w/intregrated sound (SB Live). I downloaded the Linux drv from Dell for this box. Not sure where to turn next. Thanks so much for your insight & expertise! Doug

---

### Post by mlind on 2006-03-17
you shouldn't need to install driver separately. ALSA should have compiled module
ready for this.

could you post contents of your /proc/asound/cards

---

### Post by ddavi4 on 2006-03-17
Here is the attached info from my sound driver installation routine. Not sure what I am doing wrong..... or missing in this setup?  But with great help I know I will succeed! Thanks for any help you all can provide. Doug

---

### Post by taurus on 2006-03-17
What model is your Dell machine?

---

### Post by ddavi4 on 2006-03-17
Dell OptiPlex GX1 PIII

---

