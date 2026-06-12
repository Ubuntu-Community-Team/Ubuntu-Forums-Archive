---
title: "canon pixma mp600 print driver???"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by philmiller on 2007-03-13
I am looking to make my canon pixma mp600 work on ubuntu edgy.  I went to linxprinting.org and followed their directions for my printer, but i am not sure what to do with the .rpm files i downloaded.  From what i could find out it looks like i need to install alien (which i did) so that when i open the files they are recognized.

How do i install them from there?

I am relatively new to ubuntu so any advice would be helpful if broken down to its simplest form  :)

Thanks
Phil

---

### Post by Cathead Fred on 2007-03-14
Hi philmiller,

 Sorry to hear about your problem. It sounds to me that you are half way there. Here are some links that explain how to use Alien with .rpm files.

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)

Good luck and post your progress

Cathead Fred

---

### Post by watersevenub on 2007-04-17
It seems that Canon released MP600 Linux drivers for Fedora. Have a look in:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)

In Ubuntu Edgy Eft, I've used "alien" to convert the RPMs to DEB and then "dpkg -i" to install the Debian files. Then I added a new printer with the 2.70 MP600 driver. However, for some reason the printer does not respond. I'm almost sure it will work in Fedora. Why wouldn't it work in Ubuntu?

---

### Post by philmiller on 2007-04-17
> **watersevenub said:**
> It seems that Canon released MP600 Linux drivers for Fedora. Have a look in:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)

In Ubuntu Edgy Eft, I've used "alien" to convert the RPMs to DEB and then "dpkg -i" to install the Debian files. Then I added a new printer with the 2.70 MP600 driver. However, for some reason the printer does not respond. I'm almost sure it will work in Fedora. Why wouldn't it work in Ubuntu?

Excellent.  Thanks for the heads up.  I called Canon when I first bought the printer and they told me there was no drivers for Linux, I wish they knew that this was in the works.

Lack of the ability to print has been my biggest hangup with Ubuntu.  when I get home tonight I am going to give this a shot and see how it works.  

Thanks again for helping me!

Phil

---

### Post by philmiller on 2007-04-17
I just looked closer at your link.  It takes me to the australia site which does have the Linux drivers.  Then I thought I would look at the USA site as well, and it is not there.  I wonder if that will matter.

I will let you know.

Phil

---

### Post by watersevenub on 2007-04-17
Yes, it was only released in the Australian Canon website. No idea why they don't release it everywhere!

You have a quick solution here using the MP500 drivers:
[https://answers.demo.launchpad.net/ubuntu/+ticket/3896](https://answers.demo.launchpad.net/ubuntu/+ticket/3896)

But I'm really curious why the MP600 linux drivers seem not to work in Ubuntu!:-/

---

### Post by murraj2 on 2007-07-16
I installed the MP500 drivers and it appears to work correctly. In my Printers, I have MP500-Ver.2.60 listed, but it won't print. I just tried doing the test page and I get nothing. Checking the monitor it says "Stopped: job-stopped"

I tested the printer with a photo directly off my memory stick and that works fine, and when I plugged the USB cord into my laptop it recognized the memory stick that is in the printer, so I know that it's seeing the USB connection.

Any ideas would be greatly appreciated.

---

### Post by Binton on 2007-07-24
I downloaded cnijfilter-mp600-2.70-1.i386.rpm from [http://alpha03.c-wss.com/inc/ApplServlet?SV=WWUCA900](http://alpha03.c-wss.com/inc/ApplServlet?SV=WWUCA900)

Of course its rpm and not deb which as it turns out is a fat load of good on Ubuntu so
I opened a terminal and...

$ sudo apt-get install alien
$ cd Desktop
Desktop$ sudo alien cnijfilter-mp600-2.70-1.i386.rpm
Password: whatever your password is.

A couple of scary warnings later
Warning: Skipping conversion of scripts in package cnijfilter-mp600: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
cpio: premature end of file
cnijfilter-mp600_2.70-2_i386.deb generated

This file then appeared on the desktop, I double clicked on it, and it installed.

then to System/administration/printing on menu bar

Click new printer select bjc 600 then forward, the driver is already installed so don't hit install driver or you'll start looking for ppds.

This got me printing, I wondered if this driver also handled the scanning. NO! A cursory search for scanning drivers revealed nothing very encouraging....anyone?

Apparantly HP and Epsom are better served as far as drivers are concerned.

---

