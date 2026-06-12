---
title: "ATi Drivers for x1900xt &amp; 64-bit ubuntu."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Lonz on 2006-11-12
This is my first install of linux/ubuntu before, and I've read the documentation on the website and some lnisk that came up on search. Alas I'm completely lost.

I'm using an X1900XT and have no idea where to go after trying to download the drivers from the [www.ati.com](www.ati.com) website and installing them from there. It says "installation complete" but after a restart nothing has changed ](*,) 

can someone lead me in the right direction to get them going?

thanks,
alex.

---

### Post by WalmartSniperLX on 2006-11-12
Put that driver in your home folder and follow this tutorial. Make sure you change the name of the driver in the tutorial to the name of the driver you downloaded. It worked for me even when i had the 64bit ubuntu

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

Edit: Make sure you enable all your repositories in the 'Software Properties" by checking all the channels

---

### Post by Lonz on 2006-11-12
I get to this part:

EDIT:

got round the earlier problem. However:

sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod

gives

sudo: module-assistant: command not found

---

