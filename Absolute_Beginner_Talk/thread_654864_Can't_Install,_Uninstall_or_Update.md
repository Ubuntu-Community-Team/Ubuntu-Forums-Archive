---
title: "Can't Install, Uninstall or Update"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2007-12-31
Posted this yesterday, and one suggestion was to ignore which I did.  However, I now find that I can not install, uninstall, or update anything via Synaptic.  {Get notification to upgrade Adobe Flash Plug-in installer. Click on install and get following error message: " E: tzdata: subprocess post-installation script returned error exit status 1". What does this mean? Is it important? If so, how do I correct the error.}  When I attempt to perform any of these actions I get:  : " E: tzdata: subprocess post-installation script returned error exit status 1".   I attempted to download Flash Player 9 from Adobe, but did not know how to install it once it was downloaded.  I was uncertain of the command to use in Terminal.   The simpler the instructions, the better for me as I am not a techie.
CB:

---

### Post by perlluver on 2007-12-31
From what I understand tzdata is Time Zone Data, to install flash player from source, you have to unzip the package, then open a terminal and run > ./flashplayer-installer

---

### Post by Covalent Bond on 2007-12-31
Perlluver:

Did not work.  I get the same message.  Any other suggestions?
CB

---

### Post by perlluver on 2007-12-31
I am stumped, never had that problem before.  Can always search google with that error.

---

### Post by Covalent Bond on 2007-12-31
Perlluver:

Googled the error message, and one suggestion was to change my local time to London.  Did that, and it worked.  After the updates, I changed back to EST.  Who's of thunk it!!
Thanks for the hint.
CB

---

### Post by highfructose327 on 2007-12-31
CB

bastidrazor said

> Oddly enough setting your TimeZone to Europe/London then running```
 sudo dpkg-reconfigure tzdata
``` and setting it up with your time zone works. i just ran it.. tzdata now gives no errors.


this is  the link to the forum 

[http://ubuntuforums.org/archive/index.php/t-583024.html]("http://ubuntuforums.org/archive/index.php/t-583024.html")

hope it helps

---

