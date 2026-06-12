---
title: "ip1800 Canon printer driver"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by donthavacluebuntu on 2007-08-18
Hello.

I was trying to install a printer driver for a Canon iP1800 printer.  With the help of someone else I did find and download the driver, however, when trying to install it states:


[COLOR="Navy"]Could not open "cnijfilter-ip1800series-2.70-1.i386.rpm"
Archive type not supported.[/COLOR]


Any ideas?  Yep, I am a total newb to this, however Ubuntu is really cool and I am having a great time using it.

Thanks in advance for your time!

---

### Post by gobbles414 on 2007-08-19
Hi donthavacluebuntu (I love your name),

I have had great success in Ubuntu 7.04 getting printers to work by installing them as similar printers. For example, I recently installed a Canon MP530 for a friend of mine. But when Ubuntu's New Printer wizard asked me what kind of printer I was installing, I selected MP830. The driver for the MP500 class was a waste of time.

So, my recommendation is for you to go system --> administration --> printing --> new printer (make sure any old printer installation attempts have been deleted before selecting new printer). Try different printers in the ipxxxx class. If given a choice of simple or expert driver, I recommend that you select simple. Trying all of these printers could take some time -- but certainly less time than trying to install an "official" driver from the web.

FYI, a good resource for discovering printer compatibility with Linux can be found [here]("http://openprinting.org/printer_list.cgi"). If you don't see your exact printer model, try some of the ones that are close. for you, I would look at the ip1600 and the ip1880 to start.

---

### Post by schorsch on 2007-08-19
> **donthavacluebuntu said:**
> 
[COLOR="Navy"]Could not open "cnijfilter-ip1800series-2.70-1.i386.rpm"
Archive type not supported.[/COLOR]

You can convert .rpm packages to .deb packages by using "alien"
```
sudo apt-get install alien
alien --scripts cnijfilter-ip1800series-2.70-1.i386.rpm
```
Then you will have the deb-package which can be installed via "dpkg -i" or however you like to.

---

