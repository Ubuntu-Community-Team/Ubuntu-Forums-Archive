---
title: "Struggling with flash plugin for firefox [Resolved]"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by hoosemon61 on 2007-04-21
Finally got my daughter's laptop running well with Dapper.  When visiting sites with Firefox, I get the blank panel w/puzzle piece, prompting me to install a plugin for flash.  

I tried installing by clicking on that and it goes through the routine of finding the Adobe flash plugin, asking me if I accept the license and then goes to an endless install screen with the moving progress indicator.  I've let this go for a very long time without result.  It doesn't freeze, and i can then cancel.

Next, I used the menu in firefox to look for plugins.  I got to the page listing all the available plugins and clicked on the "install now" button for flash.  It took me to a page where I could download the rpm or tar files.  

I downloaded the rpm file and followed the instructions for installing it on the site.  That didn't work as desired.  

I checked the Ubuntu Wiki and it said to rpm files aren't very Ubuntu friendly, so I installed Alien and converted it to a deb file.  

I then installed the deb file successfully.

Firefox still didn't have the plugin installed.  

When I type "about:plugins" in the firefox address bar, it says no plugins are installed.  

I read the linux support info on the firefox plugin flas download page and it told me to drag 2 of the flash files to certain folders.  I went back to the download page and downloaded the tar version.  I extracted libflashplayer.so and tried to drag it to /usr/lib/mozilla/plugins as directed and was told I'm not allowed to access that folder...


I'm running out of steam here...


Any suggestions?

My knowledge of basic command line stuff is pretty weak so assume I'm a dummy.

Thanks,

Hoosemon

---

### Post by oilchangeguy on 2007-04-21
the easiest way i've found to install it is to use automatix. go to [www.getautomatix.com](www.getautomatix.com) click on the installation tab, and click on the quick install for version 6.06. use can use automatix to install flash, and a whole lot more.

---

### Post by hoosemon61 on 2007-04-21
I'm not sure where the smilie came from, but I can't get rid of it.  The command was "about:plugins".

---

### Post by aysiu on 2007-04-21
This will help you get Flash installed:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Sef on 2007-04-21
> the easiest way i've found to install it is to use automatix. go to [www.getautomatix.com](www.getautomatix.com) click on the installation tab, and click on the quick install for version 6.06. use can use automatix to install flash, and a whole lot more.

Be careful with automatix.  It can work well, but it can also break your system, so you have to do a reinstall.  It is not supported by Ubuntu.

---

### Post by oilchangeguy on 2007-04-21
> **Sef said:**
> Be careful with automatix.  It can work well, but it can also break your system, so you have to do a reinstall.  It is not supported by Ubuntu.

show me proof that automatix has broken any system. i've used it on both of my computers with no problems.

---

### Post by hoosemon61 on 2007-04-21
Sorry, didn't mean to start an argument...

I tried the Psychocat tutorial and it worked great, thanks.

I've used Automatix on an earlier unit and it is extremely user friendly, but I'm looking to stretch my knowledge of this kind of command line stuff...

Thanks to you both!

Hoosemon

---

