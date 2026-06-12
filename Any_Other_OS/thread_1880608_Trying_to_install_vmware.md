---
title: "Trying to install vmware"
date: 2011-11-13
forum: Any Other OS
---

### Post by Randymanme on 2011-11-13
On another window, I'm at   [http://www.howtoforge.com/how-to-instal ... ux-mint-11]("http://www.howtoforge.com/how-to-install-vmware-player-on-ubuntu-11.04-linux-mint-11").  I'm at the part where falko says: 

We can start the VMware Player installation as follows:

gksudo bash ./VMware-Player-3.1.4-385536.x86_64.bundle

This will start the graphical VMware Player installation wizard. Just click your way through it: 

Well what I get is: 

randymanme@randymanme-Dimension-8300 ~ $ gksudo bash ./VMware-Player-3.1.4-385536.x86_64.bundle
randymanme@randymanme-Dimension-8300 ~ $ 

and nothing happens.  How should I now proceed?

Any assistance would be much appreciated.  Thank you.

---

### Post by ubupirate on 2011-11-14
This should help you:

[http://ubuntuforums.org/showpost.php?p=6247826&postcount=4](http://ubuntuforums.org/showpost.php?p=6247826&postcount=4)

---

### Post by Randymanme on 2011-11-14
Thank you for the direction.  Here's what I got:

randymanme@randymanme-Dimension-8300 ~ $ sudo sh Vmware-Player-3.1.5-491717.i386.bundle
[sudo] password for randymanme: 
sh: Can't open Vmware-Player-3.1.5-491717.i386.bundle
randymanme@randymanme-Dimension-8300 ~ $

---

### Post by Randymanme on 2011-11-16
I met a gentleman at last night's Ubuntu Round Table group who advised me to right-click the package and tick it as executable (which it already was), and then drag and drop it from the Nautilus window into the terminal.  The terminal charted the path by default.  I prefaced the path with  "sudo sh,"  hit "enter" and the VMware installer took care of it from there.

My thanks and appreciation to all who responded.

---

