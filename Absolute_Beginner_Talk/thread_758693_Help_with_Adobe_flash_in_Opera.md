---
title: "Help with Adobe flash in Opera"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by tonyp1969 on 2008-04-18
Hi

I downloaded and installed Flash Player but it doesn't install to Opera. It installs to  firefox fine. I tried copying the .so file manually to the Opera add in directory but was told I do not have permissions. Could anyone help?


Thanks

---

### Post by Michael.Godawski on 2008-04-18
You perhaps want to try out these installation guides:
[LIST]
[*][http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html](http://www.ubuntugeek.com/how-to-get-flash-working-in-opera-920.html)
[*][http://sysblogd.wordpress.com/2007/08/01/ubuntu-opera-flash-and-feisty-fawn/](http://sysblogd.wordpress.com/2007/08/01/ubuntu-opera-flash-and-feisty-fawn/)
[/LIST]

---

### Post by gandaran on 2008-04-18
> **tonyp1969 said:**
> Hi

I downloaded and installed Flash Player but it doesn't install to Opera. It installs to  firefox fine. I tried copying the .so file manually to the Opera add in directory but was told I do not have permissions. Could anyone help?


Thanks

what version of opera you installed? version 9.50beta works fine with the new flash, no need to install flash again as it will look for and use the mozilla plugins flash folder.
if you have a opera version 9.25, 9.26 or 9.27, the only way it works is by installing an older flash version,( adobe flash 9.0.48 ) and I recommend installing this flash in the /home/user/.opera/plugins folder (no permissions needed here) for permission to copy/paste to the file system, type ' sudo nautilus ' in a terminal.

---

### Post by tonyp1969 on 2008-04-18
> **gandaran said:**
> what version of opera you installed? version 9.50beta works fine with the new flash, no need to install flash again as it will look for and use the mozilla plugins flash folder.
if you have a opera version 9.25, 9.26 or 9.27, the only way it works is by installing an older flash version,( adobe flash 9.0.48 ) and I recommend installing this flash in the /home/user/.opera/plugins folder (no permissions needed here) for permission to copy/paste to the file system, type ' sudo nautilus ' in a terminal.

I have now installed Opera 9.50beta and still no flash.

---

### Post by gandaran on 2008-04-18
> **tonyp1969 said:**
> I have now installed Opera 9.50beta and still no flash.


if the flash is installed on the file system there should be no problem as opera looks for it there. but if it's on /home/user/.mozilla/plugins, all you have to do is copy that plugins folder to /home/user/.opera folder.

---

### Post by TeoBigusGeekus on 2008-04-18
[http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

---

