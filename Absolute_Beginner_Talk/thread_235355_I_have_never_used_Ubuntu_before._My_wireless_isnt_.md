---
title: "I have never used Ubuntu before. My wireless isnt working..."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by XenoBreak on 2006-08-12
I just got done installing Ubuntu on my second computer. I have never used any form of linux in my life so i have no idea what im doing. Everything seems to be working fine except my wireless. I pinged my other computer with the router to see if there was a connection but there was none found. Also in the network devices thing theres no wireless listed. I tried firefox anyways but it obviously did not work, lol.

---

### Post by rekahsoft on 2006-08-12
what wireless card are you using?

---

### Post by XenoBreak on 2006-08-12
Not sure how to check that..

Only thing i know is my router is a Linksys Wireless one and it came with a usb antenna box thing to plug into the other computer to recieve the connection.

---

### Post by Polygon on 2006-08-12
are you dual booting with windows by any chance? (just to see if we can get windows to see what wireless card you have)

---

### Post by XenoBreak on 2006-08-12
Nope only got Ubuntu on here

i used to have xp and the wireless worked fine on that

---

### Post by GuitarHero on 2006-08-12
We need to know the chipset of the card to find the drivers for you.  If you tell us the maker and model of the card we can find the chipset out.

---

### Post by XenoBreak on 2006-08-12
How do i find out? I dont know how with ubuntu because i know nothing about it.

---

### Post by IYY on 2006-08-13
You say your wireless device connects though USB? Try the command 'lsusb' to list all USB devices.

---

### Post by XenoBreak on 2006-08-13
ok i typed it in and got this...


"Bus 001 Device 002: ID 13b1:0006 Linksys WUSB11 v4.0 802.11b Adapter"

---

### Post by XenoBreak on 2006-08-13
I edited what i said before. Just making sure you guys see that...

---

### Post by XenoBreak on 2006-08-13
Ok so.. any ideas?

---

### Post by XenoBreak on 2006-08-13
bump :confused:

---

### Post by junglepeanut on 2006-08-13
I am pretty new so I really don't know if your wireless is covered from a basic install. You may need to download the driver first.

But lets try somethings.

Do you have ndiswrapper?

Have you tried network-admin?

If neither of those are working sometimes I find network-admin (networking in a menu on xfce I think same on other menus Ii normally cli it) can figure it out but is acting buggy so I will help it along. 

check ifconfig for all connections

check iwconfig to see wireless name if no network-admin
then if as I suspect it is eth1

sudo ifdown eth1
sudo ifup eth1

that will turn off the connection for wireless then turn it on again. If it works you will get sometime till a reset message. 

I will run this until I get it started, or mix and match these with network-admin. It seems to act funny since I am constantly switching wireless connections. But as I learn each wireless connection I know what works best for each. And so it is very fast to connect now.

Good luck.

---

### Post by XenoBreak on 2006-08-13
i dont know what ndiswrapper and network-admin is. 

heres what happened when i used those commands:

ifconfig - gave me 2 things "eth0" and "lo" both with lots of words and numbers i dont understand.

iwconfig - 3 things "lo" "eth0" and "sit0" all with "No wireless extensions" next to them.

sudo ifdown eth1 - "ifdown: interface eth1 not configured"

sudo ifup eth1 - i got lots of errors saying "no such device"


so... i dont understand anything lol

---

### Post by XenoBreak on 2006-08-13
Well i tried Sudo ifdown eth0 instead because i guess i donthave an eth1. It did some stuff, then i tried the ifup part and it did some other stuff.

Either way my wireless network adapter is not getting a signal. This meant (when i was using xp) that i needed to install the network drivers and stuff. But how to i get them without the internet? And what kind of drivers do i need with linux..

---

### Post by junglepeanut on 2006-08-20
for network-admin try or use synaptic in the menus.

sudo aptitude install network-admin

then 
you should be able to use it.

Search ndiswrapper on google and it may help you find the driver you need. I have to convey that I am at the end of my knowledge.

Jp

---

