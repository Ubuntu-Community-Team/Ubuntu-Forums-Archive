---
title: "installing wireless driver?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by robweaz on 2007-01-22
i'm not that familiar with systems other than windows....so if someone can help me i would appreciate it....i installed ubuntu but it didnt install my wireless card...the driver on the cd that i have is for windows...can i use this driver? if not then how do i go about installing a driver if i download one?

---

### Post by mikewhatever on 2007-01-22
Why do you think you need a driver? See this first [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
and this [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

---

### Post by mike.thorton on 2007-01-22
Try to get know, what is the chip of this wireless card.

Whether it is Intel, it's in common quite easy, if it is broadcom, you can try to use windows drivers using ndiswrapper (search in forum for any howto) or linux drivers (gained from reverse engineered source?) in kernel.

To discover what model of wireless card you have, try:

open terminal, write the ```
lspci
``` command.

Good luck!

---

### Post by haveacigar on 2007-01-22
I found this and was finally able to connect to the internet... its a graphical version of ndiswrapper

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.5-1ubuntu1_all.deb&md5sum=f7dead9cfd1f3bc40c425fa41e66886b&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.5-1ubuntu1_all.deb&md5sum=f7dead9cfd1f3bc40c425fa41e66886b&arch=all&type=main)

---

### Post by robweaz on 2007-01-22
i installed the driver from the inf..but it didn't work....how do i install from gz tar....and why when i try /etc/network/intefaces file i says permission denied? and are all the commands for systems like ubuntu... knoppix.....etc.....the same?

---

### Post by haveacigar on 2007-01-22
I believe that you have to extract the tar.gz file (its like a zip file)

so you have to go into the terminal and go to the file

cd Desktop

then extract the file

tar ndisfile.tar.gz

---

### Post by robweaz on 2007-01-22
well. i know that but how do i install the file because its not an inf....so i guess i have to load it in...and that i don't know how to do...........

---

### Post by CCBalla10 on 2007-01-22
start over and try this HOW-TO
```
help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
```

Then follow it step by step....

---

