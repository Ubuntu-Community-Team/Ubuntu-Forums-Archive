---
title: "Improve wifi range?"
date: 2011-09-26
forum: Any Other OS
---

### Post by wheel_walker on 2011-09-26
Is there anything I can do, software wise, to improve the range and performance of my netbooks built in wifi?  Like something that can increase the amount of electricity going to it, or something?  And are there any cavets I should know before I get into this?  Is it possible to configure it so it only uses more electricity when it's plugged in?

Also, will this somehow kill parts of my netbook?

I use Linux Mint 10 32-bit Gnome, which I think is derived from Ubuntu 10.10.

---

### Post by Lisiano on 2011-09-26
I'll put it this way, we put a human and attach a electrode to his leg, give him a small voltage (Let's say this is the normal WiFi adapter voltage), his leg will twitch but he will stand, if you give him more, he will collapse (Let's say your WiFi adapter will be fried now).
Software wise you can't do anything. The only few things you can do is use the N-technology, it allows up to 70m indoors and 200m outdoors (G supports up to 38m and 140m respectively). Also supports speeds up to 150Mbit/s per MIMO stream (Read antennae), so up to 600Mbit/s. While B allows only up to 54Mbit/s.

If going N is not an option, you can try finding a better channel. For example if you are on a crowded spot (Say channel 1 and there are 20 APs) then it would make sense to move to any of the free channels, here is how the channels lay out and overlap each other. Click for a bigger picture.
[[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/2.4_GHz_Wi-Fi_channels_%28802.11b%2Cg_WLAN%29.svg/500px-2.4_GHz_Wi-Fi_channels_%28802.11b%2Cg_WLAN%29.svg.png[/IMG]]("http://upload.wikimedia.org/wikipedia/commons/8/8c/2.4_GHz_Wi-Fi_channels_%28802.11b%2Cg_WLAN%29.svg")

Else, all I can suggest is dancing around with your netbook and trying to find a better spot.

---

### Post by wheel_walker on 2011-09-26
So should I buy another antenna at wal mart and do [this to it](http://mrintech.com/homemade-wifi-booster-extender-for-boosting-wi-fi-signal-strength-using-beer-beverage-can)?  If I should, then what antenna is cheapest/best for this, and is supported by Debian, Ubuntu 10.10, or Linux Mint 10?

---

### Post by Lisiano on 2011-09-26
Well, technically that trick will boost the signal in a certain direction, but will worsen it for others. A wireless antennae is bi-directional, meaning it doesn't care where you face it, it will spread the signal evenly. There are also directional antennas, those have a similar look but they focus the signal in a certain direction, you can "hear" it from the front, but not from the sides or back. Technically that trick will do that. You won't "hear" or "hear" it very badly from the back.

But do the math, how many "cold ones" you could drink before making a ideal reflector that would cost the same as getting a cheap WiFi adapter?
Now think that it won't do much in the long run.

Most adapters that have a Atheros or a Ralink chipset have Awesome support in Linux (From a "Grey hat" perspective BTW).
Here is a list about how to pick out a card.
[http://www.aircrack-ng.org/doku.php?id=compatible_cards](http://www.aircrack-ng.org/doku.php?id=compatible_cards)
Here is a list of good cards that work with "Hacker tools" and consecutively, with Linux.
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=3822d23ac5334e24bd2fe240ad26b35b#compatibility](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=3822d23ac5334e24bd2fe240ad26b35b#compatibility)

In short, stay away from Broadcoms and try to find one with a Atheros or a Ralink chipset, if unsure, ask us.

---

### Post by philinux on 2011-09-26
I went with 2 powerline adapters. One of which has a WiFi antenna which I put in the lounge. Works a treat.

I went with solwise.

---

### Post by Perfect Storm on 2011-09-27
Moved to Other OS/Distro Talk.

---

