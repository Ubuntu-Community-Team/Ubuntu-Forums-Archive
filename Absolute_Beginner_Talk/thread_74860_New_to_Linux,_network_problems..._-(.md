---
title: "New to Linux, network problems... :-("
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by max g on 2005-10-12
Hi, i finally got linux (Ubuntu, after failing with mepis and puppy linux) installed on my old vaio laptop, and ive been trying to get the wireless card to connect to my school's network.  is there anyway to autodetect the settings i need to connect to the network?

---

### Post by poofyhairguy on 2005-10-13
[QUOTE=max g]Hi, i finally got linux (Ubuntu, after failing with mepis and puppy linux) installed on my old vaio laptop, and ive been trying to get the wireless card to connect to my school's network.  is there anyway to autodetect the settings i need to connect to the network?[/QUOTE]


Does the network tool detect your wireless device? If so, you need to set it up. If not, you need ndiswrapper:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by towsonu2003 on 2005-10-13
[QUOTE=poofyhairguy]Does the network tool detect your wireless device? If so, you need to set it up. If not, you need ndiswrapper:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)[/QUOTE]

if "ifup wlan0" does not work for you (didnot work for me), you can also try

sudo ifconfig wlan0 up
sudo dhclient wlan0

these will be after you set up the ESSID of your wireless network.

---

### Post by max g on 2005-10-13
thanks, i finally got it set up... all i had to do was type iwconfig into the consol and get the essid fromthere... i felt stupid that all i needed was the school's network name... lol

---

