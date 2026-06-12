---
title: "HP 1020 Printer not working"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2006-12-11
I have an HP 1020 Printer, and I want to print stuff on Ubuntu.
When I try to print something, it says that it is printing, but it doesn't print anything (even after 8 hours).  When I checked the printer settings, I found two things that were odd:
[LIST=1]
[*]It said it was a network printer, even though it is hooked up to the commputer via USB.
[*]In the printer Driver selection, it showed the Driver for HP Laserjet 1022.
[/LIST]
How do I get the correct Driver and get Linux to print properly?

---

### Post by taurus on 2006-12-11
When you configured the printer, did you tell it that it's a local printer, not a network printer?  Make sure you pick the right model from the long list of printers for HP.

---

### Post by purplearcanist on 2006-12-11
I can switch the printer to local, not network from the settings menu.

But the driver for the printer is gone.  Nothing in the list that says HP Laserjet 1020. I repeat, not there.:( 
So where can I download the driver from?

---

### Post by taurus on 2006-12-11
If it doesn't have a driver for your model, pick the closest one and do a test page to see how it comes out!

---

### Post by purplearcanist on 2006-12-11
> **taurus said:**
> If it doesn't have a driver for your model, pick the closest one and do a test page to see how it comes out!
Good idea, I'll try that.  I hope one of the printers will work decently. :-)

---

### Post by taurus on 2006-12-11
HP printers are always good in Linux.  I can send all my stuff to a HP LaserJet 4200 over the network with no problem at all.

---

### Post by robertrej on 2006-12-16
> **taurus said:**
> HP printers are always good in Linux.  I can send all my stuff to a HP LaserJet 4200 over the network with no problem at all.


I had endless problems setting my HP Laserjet 1020 on Ubuntu until
I just went to the TERMINAL WINDOW and entered the following commands
and  like magic  the printer works just fine ( I love my hp laserjet and did not
want to give it up for the sake of linux)by the way Brother and Samsung do make 
linux compatiable printers .
====================================================

Install your HP LaserJet 1020 on Ubuntu

Here you’ve got a short and reliable method of installing HP LaserJet 1020 on Ubuntu (and as far as I know Debian). Works perfectly. No further configuration required.

$ sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar -zxvf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1020
$ sudo make install install-hotplug :) 


                                                                                                    Happy holidays

---

### Post by JimmyME on 2007-02-23
I've installed Ubuntu 6.10 64AMD and cannot get my HP1000 laser to work.  I've got it to work in other distros with the foo2zjs driver mentioned below.  This driver appears to be already part of 6.10.  

The printer is identified and I select the foo2 driver but nothing prints.  This happened on another distro with foo2 as well until I did make install-hotplug.

How can I make install-hotplug in 6.10 with foo2 already installed?  I tried it in several directories but could get it to work.

I'm assuming this is the problem.  Any hints appreciated.

Thanks,

Jim

---

### Post by dto on 2007-04-09
> **robertrej said:**
> I had endless problems setting my HP Laserjet 1020 on Ubuntu until I just went to the TERMINAL WINDOW and entered the following commands and  like magic  the printer works just fine 
Thank you robertrej! :)

---

### Post by theemrsweets on 2007-05-14
Thanks robertrej!!!! It worked.  Greatly appreciated

---

