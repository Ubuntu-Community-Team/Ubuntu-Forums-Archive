---
title: "Insatlling Driver LexmarkZ605"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Chickenfoot on 2006-10-13
Hey Gang,

I am installing the Z605 driver. I am working off of the page from the forums here:

[here]("http://https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605?highlight=%28lexmark%29")

I've completed steps 1 & 2:

You'll need to install alien and libstdc++5.

sudo apt-get install alien 
sudo apt-get install libstdc++5

Installation

1. Download the driver from lexmark's site ([CJLZ600LE-CUPS-1.0-1.TAR.gz])

2. Run though the following commands:

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver. 
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems.
tar -xvzf install.tar.gz # extract the contents produced by tail
sudo alien --to-deb *.rpm # convert unusable rpm packages to deb.
dpkg -i *.deb # install the debs
sudo ldconfig # refresh ubuntu to see the new libraries
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped
sudo /etc/init.d/cupsys restart # The driver is now installed. Restart the cups daemon.

Step 3 says to run:
/usr/lib/cups/backend/z600 

You should see something like:

direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer" 


However I get this:

chickenfoot@spanky:/usr/share/cups/model$ /usr/lib/cups/backend/z600
bash: /usr/lib/cups/backend/z600: No such file or directory

I think I'm SOOOO close. So what am I doing wrong?

---

### Post by Chickenfoot on 2006-10-13
OOPS!

inserted the wrong link somehow!!

The page that I am working off of is this one:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605?highlight=%28lexmark%29](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ605?highlight=%28lexmark%29)


Thank you for your support!

---

### Post by Chickenfoot on 2006-10-13
Anybody?  Bueller? Bueller? Bueller?

:confused:

---

