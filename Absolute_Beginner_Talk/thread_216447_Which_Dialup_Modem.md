---
title: "Which Dialup Modem?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-07-15
I'm giving an old computer to a friend, who has a dialup account with Peoplepc.  I use broadband and Ubuntu always automatically configures the connection...but the dialup modem is a US Robotics "5610 56k Faxmodem Winmodem", which doesn't support Linux.  I won't be able to attempt to set up the computer  for several weeks and I'm doubting I'll be able to get the US Robotics modem working.

I've done a little research and the best bet looks like an external modem, Trendnet TFM-560X, which goes for around $30USD.  Newegg has a couple of internal modems by Hummingbird(?), which sell for around $10.
I was wondering if anyone could advise me on what dialup modem(cheapest) would be the most compatible with Ubuntu?

---

### Post by editrix on 2006-07-15
Any hardware (i.e., external) modem will work. You might want to google--especially the groups--to see if one is better than another.

When you plug the thing in, remember there's a problem with disconnects. You have to comment out "auth" in /etc/ppp/options.

---

### Post by confused57 on 2006-07-15
> **editrix said:**
> Any hardware (i.e., external) modem will work. You might want to google--especially the groups--to see if one is better than another.

When you plug the thing in, remember there's a problem with disconnects. You have to comment out "auth" in /etc/ppp/options.

Thanks for the advice, probably be safer to go with an external modem...didn't know about the "#auth".

---

