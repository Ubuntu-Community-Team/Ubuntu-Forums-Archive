---
title: "Installing drivers on Ubuntu 12.04 in MacBook Pro 9,1 Mid 2012 non retina 15 inch"
date: 2012-09-15
forum: Apple Hardware Users
---

### Post by pratnala on 2012-09-15
I just installed Ubuntu 12.04 on my MacBook Pro 9,1 Mid 2012 non retina 15 inch. I installed the 4 drivers from this link [https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=precise]("https://launchpad.net/%7Emactel-support/+archive/ppa?field.series_filter=precise")  but still I can't get wireless or bluetooth to work. Even adaptive  brightness I think isn't working. Can anyone suggest where to get the  complete set of drivers?
  P.s. Additional drivers says no proprietary devices found which is weird.

---

### Post by pratnala on 2012-09-16
Can someone help please?

---

### Post by amanojyaku on 2012-09-23
I don't know about bluetooth but if you run the following commands your wifi should work:

wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
tar xf broadcom-wl-5.100.138.tar.bz2
sudo apt-get install b43-fwcutter
sudo b43-fwcutter -w "/lib/firmware" broadcom-wl-5.100.138/linux/wl_apsta.o

They are from this post which fixed the wifi on my 9,1 MBP:

[http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work](http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work)

Basically the problem is you are missing the firmware for your card, I am guessing since you didn't post any error messages or logs.

---

### Post by pratnala on 2012-10-11
> **amanojyaku said:**
> I don't know about bluetooth but if you run the following commands your wifi should work:

wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
tar xf broadcom-wl-5.100.138.tar.bz2
sudo apt-get install b43-fwcutter
sudo b43-fwcutter -w "/lib/firmware" broadcom-wl-5.100.138/linux/wl_apsta.o

They are from this post which fixed the wifi on my 9,1 MBP:

[http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work](http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work)

Basically the problem is you are missing the firmware for your card, I am guessing since you didn't post any error messages or logs.


Brilliant! This worked!! Thank you!! And how did you install nVidia's driver?

---

