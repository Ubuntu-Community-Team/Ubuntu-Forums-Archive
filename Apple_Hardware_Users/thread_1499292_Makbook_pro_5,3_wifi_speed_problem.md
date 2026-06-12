---
title: "Makbook pro 5,3 wifi speed problem"
date: 2010-06-01
forum: Apple Hardware Users
---

### Post by linux-hack on 2010-06-01
Hi there every one.. 

I need your help with a problem that I have (as the title it self explains it).

After installing ubuntu in dual boot with mac os I followed this tutorial to make everything work on my mac ([https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid))

everything works fine but I have a litle problem with the wifi speed. In Mac OSX everything works fine, I can play HD videos on the net and download at a much better speed. But when I switch to ubuntu it's rely annoying cause sometime even a web page takes time to load. And the computer is geting rely hot also when I'm on ubuntu... So I was wondering if someone can help me with that.

May be there are other wifi drivers that work for this I don't know.. 

Thanks you for your help .

---

### Post by linux-hack on 2010-06-07
No one has a little idea of how to make this a little faster ???

And about the heat problem ?? Thanks a lot too you all

---

### Post by linuxopjemac on 2010-06-07
For heat you might want to install the applesmc-dkms package from the Mactel PPA.

[https://wiki.edubuntu.org/MactelSupportTeam/PPA](https://wiki.edubuntu.org/MactelSupportTeam/PPA)

I don't know, but you could try the open source b43 driver. You have to check whether your type of card is supported by it.

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by khelben1979 on 2010-06-08
Are you sure it's only a wifi problem? I mean, is it using a fast graphics driver or a slow open source driver which slows it down as well?

---

### Post by linux-hack on 2010-06-08
First of all thank you for your help..

I installed everything that was in this how-to : [https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

So I installed the proprietary Nvidia drivers and the wifi drivers that war proposed as recommended on by my system in the install drivers window.The wifi is working but rely slow. And I think that I already have the applesmc-dkms installed ...

---

### Post by linuxopjemac on 2010-06-08
and I said that you could try the b43 open source driver, depending whether your card is supported or not.

---

### Post by linux-hack on 2010-06-08
I'll try to see and I'll get back to you :D

Thanks a lot for your help.

---

### Post by linux-hack on 2010-06-21
> **linuxopjemac said:**
> and I said that you could try the b43 open source driver, depending whether your card is supported or not.

My card is not supported :( ... so still a slow wifi :confused:
BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b]

14e4:432b  not supported

---

### Post by linuxopjemac on 2010-06-21
Don't worry, it will come. Those people work hard.

---

### Post by linux-hack on 2010-06-21
I'm sure of it :D .. that's the beauty of the linux world :D ...

But I noticed a little thing that I rely don't like .. when I turn down the lightness of the screen nothing happens but it's showing me the bar at the top of the screen.

---

### Post by sky.programming on 2010-06-21
perhaps somebody who have experenced your problem like this can give you advice.

---

### Post by linux-hack on 2010-06-22
> **sky.programming said:**
> perhaps somebody who have experenced your problem like this can give you advice.

I hope so :lolflag:

---

### Post by linux-hack on 2010-06-22
So I has a new fresh install agen in dual boot with Mac OS and the wifi this time is ok :D

---

