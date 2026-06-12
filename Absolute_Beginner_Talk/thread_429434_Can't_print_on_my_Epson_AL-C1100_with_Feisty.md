---
title: "Can't print on my Epson AL-C1100 with Feisty"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by tomele on 2007-05-01
Hello everyone,

I am making a fresh Kubuntu Feisty install right now and can't get my Epson AcuLaser C1100 printer to work.
I have followed the exact same procedure as for Dapper and Edgy, which is basically downloading driver sources from Epson website from there : [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html), then 

```
tar xzvf Epson-ALC1100-filter-1.2.tar.gz
cd Epson-ALC1100-filter-1.2/
sudo apt-get install libcupsys2-dev
/configure
make
sudo make install
sudo /etc/init.d/cupsys restart
```

then in KDE Add Printer Wizard : Local printer > usb://EPSON/AL-C1100 > ALC1100

The printer and the newly built driver do show in the wizard dialogs, but nothing happens when I try to print a test page !?
Nothing in /var/log/cups/error.log either :confused: 

Again, the exact same procedure worked without problem with Dapper, then Feisty.
Any help would be much appreciated, thanks in advance !

---

### Post by mikeyphi on 2007-05-01
Do you also need to point the 'Add Printer' wizard to the 'PPD file' for the Epson?

---

### Post by tomele on 2007-05-01
Thank you for your answer mikeyphi, I have selected the ppd file as well in the wizard (ALC1100 was actually the driver name)... but nothing still happens when I send a page to the printer...

Anyone else ?

---

### Post by ubu-for on 2007-05-01
> **tomele said:**
> Thank you for your answer mikeyphi, I have selected the ppd file as well in the wizard (ALC1100 was actually the driver name)... but nothing still happens when I send a page to the printer...

Anyone else ?

Maybe you have [this problem](http://ubuntuforums.org/showthread.php?t=413002), too?

---

### Post by tomele on 2007-05-05
Thanks for your anwser ubu-for.
The symptoms are quite similar (printer showning up but not printing, with no error message in cups log), and most probably related to newer kernel, although it's obviously not the same printer model at all.
I have posted a message into Epson Avasys' forum, who provide the linux drivers, with no answer yet.
If anyone faces the same issue, please let me know, so that I can at least confirm I'm not missing some stupid thing.

---

### Post by lsilver on 2007-05-05
I have exactly the same problem.  I managed to get it working on 6.06 with the amendments to pstoalcx11.sh that are on various posts but I get nothing on 7.04, not even the Test Page.  Any advice would be very much appreciated.

---

### Post by Marc Higgins on 2007-11-11
This is what did work for me on Gutsy

[http://ubuntuforums.org/showthread.php?p=3751422#post3751422](http://ubuntuforums.org/showthread.php?p=3751422#post3751422)

---

