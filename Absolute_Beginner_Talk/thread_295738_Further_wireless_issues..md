---
title: "Further wireless issues."
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-11-08
I had set up my wireless internet so that it was working just fine, but it was not encrypted. I now have people sharing the wireless connection with me who need the encryption enabled, and ever since I enabled it Ubuntu will not connect to the wireless network. Yes, I HAVE changed the settings to apply to the current settings, but, alas, it will not connect to my network. Any way I can fix this?

---

### Post by civetta on 2006-11-08
How are you changing your network settings? Are you using a tool like network manager or the command line? Have you tried changing your settings with iwconfig?

---

### Post by MasterOfDisaster on 2006-11-08
Are you encrypting your network with WEP or WPA?

WEP works out of the box, but I'm pretty sure that WPA needs some tweaking to work.

---

### Post by theknave on 2006-11-08
Sorry, everyone, I was picking up my mother from work and I just got back.

I've tried using both the network manager and the iwconfig (I think...that would be the same as editing the /etc/network/interfaces file [or something to that effect] right?) to no avail, it still will not work.

I'm encrypting with WEP for sure, I checked the router page with my browser.

---

### Post by civetta on 2006-11-08
Hmmm,

My limited experience prevents me from troubleshooting this, but how about trying another tool, like [Network Manager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"), or wifi radar (both in synaptic). There's also [gtk wifi]("http://www.ubuntuforums.org/forumdisplay.php?f=74").

Also, if you're changing your settings with iwconfig, try toggling your wireless interface up and down using the commands:

sudo ifup <your wireless interface>
sudo ifdown <your wireless interface>

I use Network Manager and have never had any trouble. It's an easy to use tool, lets you store passwords in the gnome keyring, and automatically looks up your preferred networks when you move between one and the other.

---

