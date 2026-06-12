---
title: "Manually set FANspeed?"
date: 2018-02-09
forum: Apple Hardware Users
---

### Post by splintercole on 2018-02-09
Hello, i am brand new to ubuntu ( and computers in general ) 

I have a very old iMac27"(2010 ish), wich i have put in a SSD, when i took out the old HDD it made the fans go at full speed constant. 
I first had windows7 installed, and i used macfans control program to manually set the fan to a lower value. (its very loud now at full speed 5500rpm )

I have serached for 2 days trying to fix it but i have given up at this time :( can anybody help me manually set down the fan speed?

I found a thread here of a similar problem , but that didnt help me: 

sudo apt-get install applesmc-dkms


somebody answered with : Hm, I believe applesmc-dkms is for Intel macs only.


 so i guess my mac is not compitable with that ^?

---

### Post by coffeecat on 2018-02-09
*Thread moved to **Apple Hardware Users**.*

Welcome to the forum.

So that forum members can better help you, please post which flavour (Ubuntu, Xubuntu, Lubuntu, etc) of Ubuntu you are using, and which release number.

If you have an iMac from about 2010, that would have an Intel CPU. However, the applesmc-dkms package comes from the [Mactel Support PPA](https://launchpad.net/~mactel-support/+archive/ubuntu/ppa), which appears to be more than moribund, and which lists no version of applesmc-dkms suitable for a currently supported release of Ubuntu. Please post a link to the thread you found. My guess is that it could be very old and for a long-obsolete version of Ubuntu.

---

### Post by leunam12 on 2018-02-09
There is a thermal sensor cable that you have to connect to the hard drive, it has to be connected in the right orientation and to the right pins on the Hard Drive. Otherwise the fans will spin at full speed. Maybe the drive is incompatible with Macs. I suggest you do some research on this.

[https://www.ifixit.com/Answers/View/85991/replace+the+hard+drive%2C+how+do+I+connect+Hard+Drive+thermal+sensor](https://www.ifixit.com/Answers/View/85991/replace+the+hard+drive%2C+how+do+I+connect+Hard+Drive+thermal+sensor)

---

### Post by splintercole on 2018-02-09
thanks for the reply, i am using ubuntu 16.04 LTS. Yes, it seems to be a Intel Core i3 550 @3,2GHz x4

This was the post i found : [https://ubuntuforums.org/showthread.php?t=1666780](https://ubuntuforums.org/showthread.php?t=1666780)

But i see now it is from 2011

---

### Post by splintercole on 2018-02-09
yes, it is incompatible because the sensor cables doesnt fit. But i knew that before i put it in ( i got it for free ) But was told to use macs fan control to manually set the fan instead, but that was on windows so now i dont know how to manually set it.

---

### Post by splintercole on 2018-02-10
Bump

---

### Post by splintercole on 2018-02-10
bump2

---

### Post by kevin160 on 2018-02-14
I use macfanctld.  There's also mbpfan at [https://github.com/dgraziotin/mbpfan](https://github.com/dgraziotin/mbpfan)

As for actually manually setting the speed without software, as root:

echo 5000 > /sys/devices/platform/applesmc.768/fan1_min
works on my mini6,2

---

