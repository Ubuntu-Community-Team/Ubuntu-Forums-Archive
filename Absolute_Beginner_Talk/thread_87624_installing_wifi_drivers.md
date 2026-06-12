---
title: "installing wifi drivers"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by danne on 2005-11-08
hi

can someone tell me how to install drivers ;) in linux. Especially the drivers for the realtek 8180 wifi driver. I downloaded it on [www.realtek.tw.com](www.realtek.tw.com) (for kernel 2.6.X) but now I don't know what I have to do next.

kind regards

danne

---

### Post by ssam on 2005-11-08
you could try searching the [wiki]("http://wiki.ubuntu.com/") to see if someone has documented how to do it.

sam

---

### Post by Mustard on 2005-11-08
These are the main How To's for wifi and ndiswrapper,

[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by jdong on 2005-11-08
NDisWrapper is not necessary.

It looks like you just need to install:

(1) build-essential
(2) gcc-3.4
(3) linux-headers-`uname -r`

using sudo apt-get install PACKAGE

then, you'll need to extract the drivers with "tar xzvf archname.tar.gz", then "cd directory_containing_drivers" (usually the tar output will help you guess the right folder name)

Then, once you're in the folder, run "make; sudo make install", enter your password when prompted.



If these instructions do not solve your problems, please post the URL to the driver file you downloaded, and we'll try to give you very specific instructions.

---

### Post by aaso on 2005-12-06
is there anyone who got the rtl8180 linux driver to work with Ubuntu (Breezy) ?

---

### Post by john280z on 2005-12-08
I have just come back from a successful test of my rtl8180 PCMCIA card in my laptop, a Compaq Armada 1550DMT running Breezy 2-6-12-9-386.
   I used the ndiswrapper (ver 1.1) that is available with Breezy and followed the instructions here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
   Note: scroll down to the part labeled "Install Windows driver" - I did NOT compile the ndiswrapper or anything else.
   I tried the realtek driver(version 173) and that almost worked but then the yellow LED on the wifi card would stop blinking. I tried today with the 154 version and all is well, I got an IP address and then ran "xchat" and also used Firefox to send an email from my Yahoo account.
   I have not tried to unplug/plug the card yet.
   My card is a no-name brand I got on ebay for $5.97 plus shipping. It shows the standard Realtek "10ec:8180" information.

---

