---
title: "Installing scanner software"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by rift400 on 2008-03-02
Hi
I'm VERY new to ubuntu. I've managed to track down some drivers for my EPSON RX630 on the epson site [http://www.epsondevelopers.com/home/linux_scanners]("http://www.epsondevelopers.com/home/linux_scanners") but it doesn't appear to list ubuntu on its supported platforms list., Can I use one of the others? If so how do I install it? A step by step guide would be greatly appreciated as I'm trying to study for upcoming exams and my brain's a bit fried...

Cheers
Justin

---

### Post by Anduu on 2008-03-02
You should try out XSane...it's in the repos.

It supports a multitude of scanners.No drivers required.

---

### Post by rift400 on 2008-03-05
I've tried xSane... it tries to search for the scanner and doesn't pick it up. Returns message 'No devices available'.

---

### Post by kellemes on 2008-03-05
Can't give you a howto.. but I can give a couple of links that may be useful.
This page shows your device works with the gutenprint-drivers.
[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX630]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX630")

This thread explains how to install the gutenprint-drivers (I assume), you can use "synaptic" to install the needed gutenprint packages.
[http://ubuntuforums.org/showthread.php?t=696567&highlight=gutenprint]("http://ubuntuforums.org/showthread.php?t=696567&highlight=gutenprint")

This page is from the Ubuntu documentation, may be interesting to read.
[https://help.ubuntu.com/7.10/printing/C/index.html]("https://help.ubuntu.com/7.10/printing/C/index.html")

I'm not promising it'll work but who knows..;-)

---

### Post by rift400 on 2008-03-05
Thanks for the advice. I've managed to install the libsane-extras which should theoretically allow my scanner to work. The only problem now is that ubuntu is not allowing me to edit /etc/sane.d/dll.conf. It comes up with -

Could not save the file /etc/sane.d/dll.conf.

You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.

Any ideas?

---

### Post by kellemes on 2008-03-05
> **rift400 said:**
> Thanks for the advice. I've managed to install the libsane-extras which should theoretically allow my scanner to work. The only problem now is that ubuntu is not allowing me to edit /etc/sane.d/dll.conf. It comes up with -

Could not save the file /etc/sane.d/dll.conf.

You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.

Any ideas?


You need to get root-privileges to edit system-files, like so..
from terminal..
```
sudo gedit /etc/sane.d/dll.conf
```
"sudo" will ask for your password so you get root-privileges.
**or** you can do..
```
gksudo nautilus
```
now you can browse to the file and edit/save it as root.

Edit: some reading material.. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by rift400 on 2008-03-05
OK the editing suggestion worked :) Thanks. Now I've just realised that the RX630 scanner isn't supported in the SANE list. I got a redirect back to the list of drivers I had found earlier at [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do")

Problems are -
1. I have no idea which selection to make to download the driver for Ubuntu (can I use debian?)
2. I have no idea how to install it once I get it. 

I'm really grateful for your help... If I wasn't so pressed for time, I honestly would try to find it in the manuals...

Cheers

---

