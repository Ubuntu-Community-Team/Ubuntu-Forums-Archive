---
title: "Wireless help..."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by blackstripes on 2008-01-15
I have recently installed Ubuntu 7.10 on a Toshiba a205-s5804 and have been having a really hard time getting my wireless card to work consistently.  I have been doing tons of reading lately and have learned a lot about this OS.  Anyway, the card in this is a Realtek 8187b and I have found some modified drivers that I am using.  It does not support WPA which isn't an issue, but as soon as I reboot my laptop the card does not work again.  When I boot the laptop I need to run a 'makedrv' file and then a file called 'wlan0up'.  

I have tried figuring out how to change /etc/network/interfaces so that these files are run upon startup, but I can't figure it out.

Also, I have seen people recommend ndiswrapper + WIN98 drivers, but I can't figure that out either.

I apologize for the long post, but I have never had ANY experience with Linux prior to 3 days ago.  Any help would be much appreciated! :)

---

### Post by sauronsmatrix on 2008-01-18
get the windows drivers, and use ndiswrapper to install them. post the outputs here, any error messages, etc.

use my post as a basic guideline:
[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)

the only thing different should be which drivers you use.

---

