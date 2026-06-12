---
title: "CUPS server cannot be contacted ???"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-02-21
Just installed my new HP C5140 All in one printer last night with CUPS and everything went smooth as silk. Printed test page good and all went well. It is hooked to my network via ethernet cable and all three comps can ping each other, the router, and the printer with no problem. Logged on tonight and wanted to print something, but received error of "CUPS server cannot be contacted". Nothing has been changed since last night, so I am wondering what went wrong. I have a Toshiba Satellite Pro laptop, 768 Ram, 40 Gig HD, with dual boot Ubuntu 6.06 and XP. Any ideas on why I keep getting this message. I can't even try and reconfigure the printer from System>Admin>Printing, as this is where I get the error message. Please help a shiny newb!!!

---

### Post by NewOldTimer on 2007-02-21
try this  

sudo dpkg-reconfigure cupsys
sudo /etc/init.d/cupsys restart

then post what happens

---

### Post by jerrynewt on 2007-02-21
That did the trick --- Thank you so much -- this forum is the best !

---

### Post by NewOldTimer on 2007-02-21
Hang in there, it gets even better:)

---

### Post by jerrynewt on 2007-02-22
I turned the comp off for about two hours and then logged back on and the same thing is happening again -- cannot connect to CUPS server. Do I have to reconfigure the cups service every time I log in ??

---

### Post by NewOldTimer on 2007-02-22
I'm out of answers for you sorry, maybe this will help..
[http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

---

### Post by tgalati4 on 2007-02-22
Make sure your /etc/hosts file contains the IP addresses  and hostnames for the machines that want to print.  Include 127.0.1.1 myhostname if you are using DHCP.  CUPS gets wonky when it can't find hostnames.

Share with us interesting error messages in /var/log/cups

Spend time to master CUPS and you will gain a new appreciation for printing under Linux and the mac.  There are lots of tutorials on the forum, search CUPS.

Pay it forward by helping other users who have problems with Windows.

---

