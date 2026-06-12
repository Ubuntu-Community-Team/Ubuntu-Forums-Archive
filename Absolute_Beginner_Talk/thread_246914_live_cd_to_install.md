---
title: "live cd to install"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by TrIde2188 on 2006-08-29
I was wodnierng, i seme to ahve lsot my isntall cd for ubuntu 

cna you still use the live cd to instlal it onto the HDD?

also the gui for some reason was just a blank screen with the cursor.. so i alt+ctrl+f2'd into the command line could anyone tlel me how to install ubuntu via that?

many thanks in advance

-TrIde

---

### Post by aysiu on 2006-08-30
If the live CD is for 6.06 (Dapper Drake), then, yes. Install following these instructions: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

If the live CD is for 5.10 (Breezy Badger), then, no.

Booting the live CD just gives you a blank screen? This won't install Ubuntu, but it may help you get a working GUI: Control-Alt-F1 and ```
sudo dpkg-reconfigure xserver-xorg
``` Control-Alt-F1, Control-Alt-Backspace.

---

### Post by TrIde2188 on 2006-08-30
tahnks =] worked out well cheers!

---

