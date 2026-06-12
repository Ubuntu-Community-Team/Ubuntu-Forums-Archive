---
title: "Wireless"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jamiehd on 2007-01-06
I have just installed linux on my laptop as a dual boot with windows.

However I cannot seem to get my wireless network card to work. I cannot find a driver for it. It is an Intel® Pro Wireless 3945 802.11a/b/g Mini PCI Wireless LAN Card for Core 2 Duo Processors. Can anyone help please. :)

---

### Post by notepad on 2007-01-06
i think youll find drivers are installed for your adaptor already.
follow this guide because it worked for me.

[www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by jamiehd on 2007-01-06
No. the comptuer can't even find the wireless card

---

### Post by geekygreen on 2007-01-06
Here is a[ similar thread.]("http://ubuntuforums.org/showthread.php?t=332008")...perhaps there is something usefull there...

---

### Post by jamiehd on 2007-01-06
No :(

I've tried looking the DELL website, but I can only find drivers for windows. I tried the steps in that link, but the terminal told me this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by petermck on 2007-01-06
There's a guide in the Community docs section [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") which could help.

---

### Post by notepad on 2007-01-16
did you follow the instructions at debianadmin.com? that worked for me. which version of ubuntu are you using? im on 6.10 and it supported my wireless out of the box. i just needed to install network-manager etc to make it work.

---

### Post by nonpareilpearl on 2007-01-16
Check your card's compatibility [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53"). If the card isn't compatible, but the driver can be configured appropriately, then there should be a link to the proper instructions. Good luck!

---

### Post by Duppy on 2007-01-16
Check the wireless card is on?

eg. Fn key + F3

---

