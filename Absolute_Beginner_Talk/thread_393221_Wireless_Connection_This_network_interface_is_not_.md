---
title: "Wireless Connection: This network interface is not configured"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by John Thomas on 2007-03-25
I just 2 days ago installed ubuntu 6.10 in my "new" IBM ThinkPad T23 laptop I got from ebay.  It came with an AirLink101 USB wireless device.  I know there's no point in going to the library (where they have free wireless internet service) to try it out until I get the device configured.  From reading around, it seems I probably have to get a driver set up for the thing.  Drivers are chipset-specific, I think.  I did lsusb in terminal, and it reports

Bus 2, device 2: ID 0ace:1215 ZyDAS

I think that's the chipset name but I'm not sure.  My question is, where do I go from here?

I'm used to doing terminal things from using the Terminal program on my Mac desktop's OS X, but sometimes I'm thrown by official ubuntu instructions that include API and other 3-letter abbreviations.  I'm a raw newbie when it comes to this laptop, ubuntu and wireless stuff.

Thanks for anything you can tell me.

BTW, I'm NOT using Edubuntu, whatever that might be.  Probably something I have to edit in my profile.

---

### Post by Kamu on 2007-03-25
well, a few things you can do to see if the device is picked up by your system after plugging it in is to run the following command in the terminal:
iwconfig

and also to look in the file /etc/network/interfaces

Please post the results of these two actions here so we can help you assess the status of your wireless.

---

### Post by John Thomas on 2007-03-26
> **Kamu said:**
> well, a few things you can do to see if the device is picked up by your system after plugging it in is to run the following command in the terminal:
iwconfig

and also to look in the file /etc/network/interfaces

Thanks for getting back to me so quickly, Kamu.

Please post the results of these two actions here so we can help you assess the status of your wireless.

eth1      802.11g zd1211  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I reckon it sees the Airlink101 all right.

johnthomas@johns-laptop:~$ file /etc/network/interfaces
/etc/network/interfaces: ASCII text

---

### Post by Kamu on 2007-03-26
Yup, it sees a wireless card alright.  That doesn't guarantee you will be able to connect but your odds are good.

For your information, when I said "to look in the file /etc/network/interfaces" I meant print out the ASCII content to the screen, which you can do in many ways, a few of which are:
cat /etc/network/interfaces
less /etc/network/interfaces
more /etc/network/interfaces
or you can open the file in your favorite text editor, gedit, vi, emacs, nano, etc. 

Anyway, we know the card is picked up now, I wish you luck with trying to use it.  Don't hesitate to come back to the forums if you run into any problems with that!

---

### Post by John Thomas on 2007-03-27
> **Kamu said:**
> Yup, it sees a wireless card alright.  That doesn't guarantee you will be able to connect but your odds are good.

For your information, when I said "to look in the file /etc/network/interfaces" I meant print out the ASCII content to the screen, which you can do in many ways, a few of which are:
cat /etc/network/interfaces
less /etc/network/interfaces
more /etc/network/interfaces
or you can open the file in your favorite text editor, gedit, vi, emacs, nano, etc. 

Anyway, we know the card is picked up now, I wish you luck with trying to use it.  Don't hesitate to come back to the forums if you run into any problems with that!

OK.  Thanks, Kamu.  I still don't know just what to do next.  I suppose, as I did before, that I have to configure a driver for the card.  I downloaded a Linux driver for the wireless card from the AirLink's support team (the guy said it was definitely NOT supported).  I will look around in this forum for installation procedures.

---

### Post by Doug11 on 2007-03-27
try typing this in your terminal>>>  sudo gedit /etc/network/interfaces        and just post what comes up,,but just don't change anything in it just yet.

---

### Post by John Thomas on 2007-04-01
Turns out the AirLink is supported out of the box in Edgy, thanks to the nice people at Zydas who have released the necessary Linux driver(s).  Just today I finally got online with it.

I tried the Airlink101 wifi dongle in the ThinkPad laptop today in Panera, a sandwich shop with a free wifi connection here in Hamilton.  After doing a sudo iwlist eth1 scan command, and then configuring the Networking administration application with only the ESSID of "PANERA" (left DHCP to resolve the addresses), at first I got a browser "Can't find the server" error.  After clicking the Try Again button a couple times, it did finally connect and I was online, for free, in the sandwich shop.

I then decided to try another ESSID from the iwlist scan, the Barnes & Noble next door.  I reconfigured eth1 in Networking again, then went to the browser again, but this time all I got was that 'can't find the server' error, no matter what I tried.  Even tried going back to the first ESSID (PANERA), and I even went next door to Barnes & Noble.  No help.  Do you think I should have restarted the laptop between connections?

What do you think this browser error means?  I also tried to get my email using the Ubuntu default mail app (forget the name of it just now), and I got a similar "CAN'T CONNECT" kind of error.  I noticed plenty of other wireless users in the sandwich shop who were having no such errors (using Windows), and one line in the output from the iwlist command stated that the signals were 100 out of 100.  That means 'strong,' right?

Any ideas?

=========================================
John Thomas (new to Ubuntu & wireless)
New Jersey
IBM ThinkPad T23
AirLink101 (AWLL3026)
Edgy eft

---

### Post by John Thomas on 2007-04-01
P.S. I found a book that has been very helpful: "Ubuntu Linux Bible" by William von Hagen.  From his chapter on wireless I deduced that my original "This network is not configured" error is no error at all.  It just means that the system needs more info.

---

