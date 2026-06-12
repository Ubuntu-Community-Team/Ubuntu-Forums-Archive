---
title: "canon bjc pixma 4200 driver?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-05-16
[http://software.canon-europe.com/software/0024302.asp](http://software.canon-europe.com/software/0024302.asp)
how do i install it?
i've tried plugging it in and adding a printer and upon selecting pixma4200 it recommends the 600 driver and that doesnt work.a full size image is a quarter of the page and the colour is screwed up.
help me please guys.alternative driver or link/guide/info on how to get this to work please:(
cheers

---

### Post by Kobalt on 2007-05-16
Check this out : [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)

---

### Post by ellis rowell on 2007-05-16
I am puzzled by the model number/ID is it a bjc4200 or a Pixma IP4200. I have a Pixma IP1600 and have been unable to get any driver to work it. It looks as if I shall be giving it to a local charity, it's a pity as it's a damned good printer. However, my Epson Stylus C680 which never did print good photos under the Windows OS, now prints to a very high quality under the CUPS driver.

---

### Post by keef247 on 2007-05-16
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200)
this is really comfusing me...
> 7. Make sure the library links are correct. /usr/lib/libtiff.so.3 should point to /usr/lib/libtiff.so.4 (or to the same thing as /usr/lib/libtiff.so.4 points to) If not, type:

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 

This is the important part! The iP4200 driver wants to use libtiff.so.3, but that is an old version. We fix this by making libtiff.so.3 a link to libtiff.so.4.

Also, /usr/lib/libpng.so.3 should point to /usr/lib/libpng.so If not, type:

sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3 

and /usr/lib/libxml2.so.2 should point to /usr/lib/libxml.so.1 If not, type:

sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1 


make sure what is what?and how do i do this it doesn't tell me to open up ... and click on ... and go to ... section in ...?
get my point?
i just went through it as if they were pointing to whatever...
isn't printing though and made sure its on a4...
please help guys...

it just puts a job into the print que and disappears...

---

### Post by Kobalt on 2007-05-17
When you turn your printer on, then turn on your computer afterwards, and go to System > Admin. > Printing : when you click on New Printer and go through the wizard, does it recognize your printer ? If not, what interface is it you use : USB, LPT cable, etc. ?

PS: do not PM members in order to get answers to your threads, these are huge forums and we all try to do our best.

---

### Post by freesitebuilder on 2007-05-17
[http://www.turboprint.info/](http://www.turboprint.info/) driver supports all these canon printers you can try it free, and if it suits upgrade for about £20 which may be cheaper than buying a new pritner! It works OK on my IP3000.

---

### Post by keef247 on 2007-05-17
it displays it as connected to usb with direct monitoring etc etc.
so yeah detected just wont work!

---

### Post by Kobalt on 2007-05-17
Let's try something else then. Go to System > Admin. > Printing and remove your printer completely. Open your sources.list file ```
gksu gedit /etc/apt/sources.list
```Add the following part at the end > deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./And run these commands in order to install the drivers : ```
sudo apt-get update
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```
Now go back to System > Admin. > Printing and add your printer. 

I hope it helps.

---

