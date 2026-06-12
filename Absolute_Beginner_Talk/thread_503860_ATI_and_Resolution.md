---
title: "ATI and Resolution"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Nexus... on 2007-07-18
Hey before I start I love Ubuntu Feisty Fawn made the permanent switch the other day, when I used the Live CD I spotted things that I didn't know how to fix but at the time wasn't thinking of a permanent  switch but now I have I would like to get these sorted:

Installing my ATI Radeon 9250. Now I have been on the ATI site located Linux drivers and download but when I try to install them (by following the given instructions also on their site I get this:

nexus@Venom:~/Desktop/ATI$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8..................................................................... ........................................................................... ........................................................................... ........................................................................... ........................................................................... ........................................................................... .........................
-e ==================================================
-e ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
nexus@Venom:~/Desktop/ATI$ ls -lt
total 52784
-rw-r--r-- 1 nexus nexus 53989404 2007-07-17 20:36 ati-driver-installer-8.28.8.run
nexus@Venom:~/Desktop/ATI$ 

And doesn't carry on because of the error.

The other problem was getting the resolution of 1440x900, I edited the xorg file (Can't remember the name of it sorry) it worked fine but when I restarted it reverted back to defaults.

I have looked thorugh the forum and followed steps but some of them have not worked sorry and thank you :)

---

### Post by w4ett on 2007-07-18
The 9200 and 9250 (both RV280 GPU based) cards are poorly supported by ATI....I always had better luck with the xorg ati driver...(I even got the Feisty desktop effects working well)

I recommend you stick with the xorg driver. From the terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

and reset the driver.  PLUS in your xorg.conf, make sure your desired resolution is listed first in each line of you 'Monitor' section.

---

