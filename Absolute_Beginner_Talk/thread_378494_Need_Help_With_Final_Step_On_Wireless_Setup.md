---
title: "Need Help With Final Step On Wireless Setup"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by skeating on 2007-03-07
Hello.

  I am relatively new to Ubuntu (I have used Debian for several months some years ago), and I have properly run NDisWrapper and configured my wireless card (which is a TRENDnet TEW-423PI type B).

  Whenever I run ndiswrapper -l from the terminal, it shows as the driver and hardware being properly loaded, however when I run the 'iwconfig' command, i only get the following items returned:

eth0: no wireless extensions

lan0: no wireless extensions

sit0: no wireless extensions

or something to that effect (those are the three options).

Is there some reason that ndiswrapper didn't properly mount/setup wlan0?

I can use the wireless connection just fine with my laptop, and am currently "hardwired" to the hub  via CAT5 cable for my ubuntu box.

Thanks!

---

### Post by bobbagoose on 2007-03-07
I am a beginner at this, but may be able to help.
I was in the same position, but I did the following, and eventually got things going.

Try entering the following;

ndiswrapper -m

I think this adds the ndiswrapper to modprobe, which I get the impression contains a list of all hardware configs, although I'm not certain.

Also install wifi-radar, i think you can do this with synaptic, or try;

sudo apt-get install wifi-radar

this will give you a gui based wifi tool, seekign out available networks, and listing them for you to connect and configure.

Also restart.

I thought mine wasn't working, but a simple restart kicked it into action.

---

