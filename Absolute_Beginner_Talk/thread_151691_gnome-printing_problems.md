---
title: "gnome-printing problems"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by icaro on 2006-03-28
Hi,

First of all, this is my first message in the ubuntu forums so I would like to send a greeting to everyone.

I have a problem installing a printer. After installing the driver for the usb-printer lexmark z615 in a ubuntu Hoary, the gnome-printing frontend for cups doesn't work and it doesn't show any error message.


I wouldn't like have to change or upgrade the OS because I have to admin that by telephone from spain to a non-profit school in Colombia without inet conection and it could be too hard.

Thanks a lot.

Icaro

---

### Post by Pragmatist on 2006-03-28
You can get the driver from lexmark's website:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:433:0:0&searchLang=en&os_group=Redhat&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:433:0:0&searchLang=en&os_group=Redhat&target=)

The driver is distributed as a "tarball", so after you download, you'll need to unpack it like this (in a terminal type):
```
tar xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

Now there should a new directory with a similar name. Change to this new directory:
```
cd directory
```

Now read the README file and INSTALL file if there is one.  Probably the instructions will be to do this:
```
./configure
```
then
```
make
```
then
```
sudo make install
```

But read the README first!  Sometimes there are other things that must be done first.

---

### Post by pbaehr on 2006-03-28
Also, if you don't already have it, I think you'll need to run
```
apt-get install build-essentials
```
to grab the bits you need to compile code.

---

