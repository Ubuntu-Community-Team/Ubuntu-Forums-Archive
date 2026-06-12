---
title: "missing connection options"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by bobtom on 2007-08-09
I recently installed Ununtu(fiestyfawn) on two older Dell laptops. The specs on the laptops are;

Dell Latitude PIII  850MGz  256MB ram
Dell Inspirion  PIII  1Gig  256MB ram

both computers have the same input plugs as my Dell Precision M-50 ( a small on for telephone(dialup) and a wider one which I use for microwave delivered high speed internet)

I have XP on the M-50 and it works fine (of course it locks up in the traditional Windows way, but I'm used to that after years of Windows experience)

My problem is;

When I open up the Network Settings on the GUI I get only one option, Modem connection. According to the book I'm reading, there should be three options; Modem, Wired, and Wireless. Where are my other options. Do these older computers have the input plugs, yet no internal devices to handle wireless or wired connections?

---

### Post by lisati on 2007-08-09
Is the information at [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html) of any help?

---

### Post by bobtom on 2007-08-09
Thank you so much for your suggestion, but the options in the network settings window of the GUI are missing two of the icons, one of which I need to proceed. That would be the wired connection icon. Since I don't have dial-up I can't use the only option that it is giving me; the dial-up option. What I want to know is why does my options window for network settings only contain one option. Where are the wireless and wired options?:(

---

### Post by MenZa on 2007-08-09
Which laptops are these? Not Latitude C300s by chance?

---

### Post by bobtom on 2007-08-09
The Latitude's model number from the bottom of the case is PP01L

---

### Post by bobtom on 2007-08-11
Well,  I finally noticed that it said C 600 in another location. Sorry about the confusion!

---

### Post by bobtom on 2007-08-13
:) I believe that I have solved my own problem! I got an old PIII  desktop computer from my collection of legacy hardware(my junk pile) and put a couple of extra ram cards in (3x128) and booted Ubuntu(fiestyfawn). When I went into network settings there was the icon for wired connection! Missing was the wireless icon. Now my guess is the reason the laptop didn't have the icons needed for wired connection was the absence of a card in the laptop to facilitate this type of connection.(or I guess it could be a missing driver for the card if it exists in the laptop.) what do you guys think?   bt

---

### Post by jimrz on 2007-08-13
> **bobtom said:**
> :) I believe that I have solved my own problem! I got an old PIII  desktop computer from my collection of legacy hardware(my junk pile) and put a couple of extra ram cards in (3x128) and booted Ubuntu(fiestyfawn). When I went into network settings there was the icon for wired connection! Missing was the wireless icon. Now my guess is the reason the laptop didn't have the icons needed for wired connection was the absence of a card in the laptop to facilitate this type of connection.(or I guess it could be a missing driver for the card if it exists in the laptop.) what do you guys think?   bt

you could check the Dell site to see if that model even had an option for on-board wifi and:

- if so, you might try their support site using the serial #'s to find out if/what card each originally hod

- if not, get a pcmia card, be sure to research which work well with ubuntu before purchase. I have had very good results with my Netgear WG511T (the T is important, as the WG511 model does not fare as well) on my old TP 600x

---

