---
title: "[SOLVED] i guess it's my wifi problem turn"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-06-06
Seeing how this is the place to go for wifi problems i'll start off with saying that i can actually connect to wifi! hooray! However, WPA/WPA2 gives me problems... a lot of problems

I get disconnected all of the time.  constantly.  this doesn't happen on unsecure or WEP tho...

I currently have installed the following drivers/firmware for my Intel ProsetWireless 2200BG card

ipw2200-1.2.0 
ipw2200-fw-3.0
ieee80211-1.2.17

all from sf.net

i had a lot of problems installing them, but they seem to be in place now... not sure how to check on that...

Why can I not stay connected for more than a few minutes, after it takes me 3-5 attempts to connect?

Also, i'm using xubuntu 7.04 and network-manager-gnome to configure my connections

---

### Post by hillbilly on 2007-06-06
If you are using Fiesty, I did not have to install the ipw2200 drivers or firmware. It worked out of the box. And I had not problems with WPA (personal). havent tried to connect to any other wi-fi though.

---

### Post by miatawnt2b on 2007-06-07
I too (and others here at work) have this same WPA/WPA2 problem with the 2200bg on both ubuntu and fedora.    Any other wireless seems fine, but when we try to connect to WPA enterprise networks, it's either impossible to connect, or it connects for anywhere between 1-10 min and disconnects.  I have installed an intel 2915abg card just 30 minutes ago and it works perfectly.  The 2915abg card uses the same ipw2200 drivers.

Would love to get a real answer on this.

-J

---

### Post by miatawnt2b on 2007-06-07
Guy I work with actually had an idea here about this.  Why not download the latest windows driver from the intel website and try to use the ndiswrapper instead of the ipw2200 drivers.  The windows drivers had this same problem about a year ago and released a driver which fixed it. I wonder if using this driver with the ndiswrapper would fix things.

-J

---

