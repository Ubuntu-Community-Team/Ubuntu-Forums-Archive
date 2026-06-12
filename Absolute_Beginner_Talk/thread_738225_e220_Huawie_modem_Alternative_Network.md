---
title: "e220 Huawie modem Alternative Network?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by vk2ezq on 2008-03-28
I have a E220 bought outright in New Zealand and used on vodafone 3G.
Local shop in SW London is telling me it will not work in London.
It should not be locked to vodafone because I bought it outright for just over £100 equivalent in NZ and it was used with a PAYG plan only.

What can I do to test it?
It seemed to me that a shop or someone with a SIM should be able to test it?

---

### Post by tranquito on 2008-03-28
There has been a lot of problems with that modem. I'm a bit of a n00b but I managed to get it running on my friends Ubuntu 7.0 with three Ireland. I'll give you a hand. Just gotta look for some stuff first.

---

### Post by tranquito on 2008-03-28
Are you running it using wvdial? If so, open a terminal snd type "sudo gedit wvdial.conf" to edit the configuration for wvdial.
It should look something like this but ask vodafone for the settings specific to your region, or look them up.
[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","isp.vodafone.ie";

Also check this out for more help:
[http://the.taoofmac.com/space/Huawei/E220](http://the.taoofmac.com/space/Huawei/E220)

---

### Post by annonymouse on 2008-03-28
im using ubuntu gutsy 7.10 

first off your probs gonna need these repositories 

code: 

sudo apt-get install python-dbus python-twisted python-serial python-glade2 python-pysqlite2 wvdial nozomi-source python-notify python-gnome2-extras xdg-utils python-tz 



downloaded the Vodafone Mobile Connect Card Driver for Linux 1.99.17 (Debian Package). 

then run (your current working directory needs to be the same directory containing the file you just downloaded.) 

dpkg -i vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb 

then go to 
/usr/bin/vodafone-mobile-connect-card-driver-for-linux 

when the dashboard opens go into the tools profiles and creat a new profile username web password web prefered conection 3g and chap authentication 

you can also get into the dashboard from applications> internet 



let me know how u get on dont know how much help with error codes etc as this is beta software but on a e220 card should be fine the office card works and so does my girlfriends

---

### Post by SneakyBooBoo on 2008-03-29
is it possible to run this app on a modem thats on a different network, like 3?

---

### Post by vk2ezq on 2008-03-30
Vodafone shop is telling me that I have to buy a new E220 to get a SIM card for 3Gmobile broadband.
Another shop is telling me that E220 will not work at all although it is the same thing.
Putting a vodafone prepay phone simcard in the E220 and computer message says vodafone UK - so it seems to be working but cant afford prepay on 3G it about 5pounds per Megabyte!

---

### Post by annonymouse on 2008-03-31
u can flash ur e220 card to non network specific thik this is done in windows  a friend did mine  also update it to 7.2  speed  for  hsdpa speeds 


[http://en.wikinerds.org/index.php/Hacking_the_Huawei_E220](http://en.wikinerds.org/index.php/Hacking_the_Huawei_E220)

might be helpful for u

---

