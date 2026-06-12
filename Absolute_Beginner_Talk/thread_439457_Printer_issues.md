---
title: "Printer issues"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Celegorm on 2007-05-10
I'm having trouble getting my printer to work with my installation of Feisty. I have an HP Deskjet D4160 and added the printer through gnome-cups, but it won't print. It'll show a print job but nothing happens. I did find one site with a linux printer compatibilty list which indicated my printer works partially with linux (link: [http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D4160](http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D4160)), but I really have no idea what to try from here.

edit- I'm not exactly sure what I tried that worked, but it prints now. Thanks for all the help.

---

### Post by fakie_flip on 2007-05-10
This guy got his working (same printer). Why don't you do what he did, and if you still have some problems, you could ask him.

[http://ubuntuforums.org/showpost.php?p=2127842&postcount=4](http://ubuntuforums.org/showpost.php?p=2127842&postcount=4)

---

### Post by fakie_flip on 2007-05-10
Try searching the forums first. I searched, and here is what I found.

[http://ubuntuforums.org/showthread.php?t=365626&highlight=D4160](http://ubuntuforums.org/showthread.php?t=365626&highlight=D4160)

---

### Post by Celegorm on 2007-05-10
Well I tried installing the latest version of HPLIP from [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html) but the installer gives me this error after checking for missing dependencies:

error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.

Which really makes no sense to me as I am currently connected to the network.

---

### Post by canadianwriterman on 2007-05-10
Try it again. I just downloaded the file, but it took a few tries to connect. It will download a .run file. Click on the downloaded file and select Properties>Permissions>Execute and click the box for Allow executing file as program. Then click on the file and when the dialogue appears, select Run in terminal. Then you should be set.

---

### Post by fakie_flip on 2007-05-11
Did you get it working?

---

### Post by ramjet_1953 on 2007-05-11
When they released Feisty 7.04, they forget to include [COLOR="Blue"]python-qt3[/COLOR] as part of the standard install.

HPLIP requires it to work.

Type this in a terminal:

[COLOR="Red"]sudo apt-get install python-qt3
[/COLOR]
After this has loaded, type in this:

[COLOR="Red"]sudo hp-setup[/COLOR]

Hopefully, this will work for you.

Regards,
Roger :cool:

---

### Post by frenchy64 on 2007-05-12
> **ramjet_1953 said:**
> When they released Feisty 7.04, they forget to include [COLOR="Blue"]python-qt3[/COLOR] as part of the standard install.

HPLIP requires it to work.

Type this in a terminal:

[COLOR="Red"]sudo apt-get install python-qt3
[/COLOR]
After this has loaded, type in this:

[COLOR="Red"]sudo hp-setup[/COLOR]

Hopefully, this will work for you.

Regards,
Roger :cool:
Thankyou sooo much, works a treat! :D

---

