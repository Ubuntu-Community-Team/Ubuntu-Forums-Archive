---
title: "need help with UBUNTU-SANE scanner error"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by valis1234 on 2006-05-14
My new Ubuntu system tells me; "error Failed to open device 'gt68:libusb:001:002'; invalid argument", when I click on Applications, Graphics, XSANE Image scanning program to use a Mustek 1200 ub plus (USB) scanner. I probably have to tell the command line something else, but I don't know anything about command lines in Linux or Ubuntu. I just got this machine and could use some help.](*,)

---

### Post by Sef on 2006-05-14
What exactly is your model?

Here's a link to how one person got it running:

[http://www.linuxquestions.org/questions/showthread.php?t=178927]("http://www.linuxquestions.org/questions/showthread.php?t=178927")

Here's a link to the sane-project:

[http://sane-project.org/cgi-bin/driver.pl?manu=mustek&model=1200&bus=any&v=&p=]("http://sane-project.org/cgi-bin/driver.pl?manu=mustek&model=1200&bus=any&v=&p=")

---

### Post by claydoh on 2006-05-14
You will need a firmware file, which is on your driver cd, but is easily downloaded from here:
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
Look for your model and find the firmware file there, plus a note on a needed edit to /etc/sane.d/gt65xx.conf
If I have your model right, you need to uncomment  the line that reads:
#override "mustek-scanexpress-1200-ub-plus"
so it looks like this:
override "mustek-scanexpress-1200-ub-plus"
(simply remove the "#", which marks the line as a comment and not a line to be read)
You will need to place the firmware file in /usr/share/sane/gt68xx/
```
 sudo cp my_firmware_file.usb /usr/share/sane/gt68xx/
```

---

