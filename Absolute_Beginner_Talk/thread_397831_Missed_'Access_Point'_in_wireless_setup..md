---
title: "Missed 'Access Point' in wireless setup."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by jmattj on 2007-03-31
I have installed ubuntu 6.10 this week, and I was amazed and happy that it successfully handled the drivers for all of my hardware components. automatically.

There was a point durring my install, when it had found my  D-Link DWL-520 AirPlus  wireless network card,  where I needed to fill our some configuration information.     I think that I remember looking at the 'Access Point' field, and thinking that... I'll come back to that question.  I don't think I ever did.

I have loaded the program 'wireless radar', and using it I can connect to my router, but I am not able to connect to the internet.    Sure enough this program lists my 'Access Point' as empty.    That is when I started remembering the missed install steps about.

Can someone advise me on how to update the 'Access Point' in my wireless configuration.

Thanks a lot.
Matt

---

### Post by Roelski on 2007-04-03
Give the following a try (don't take my word for it - am newbee too!):

1. plug in the adapter - it should auto-detect
2. open a terminal and run ```
ifconfig -a 
```.  This command gives you the same info a the Win-command "ipconfig /all".  See if your device is properly listed and remember the ID it received (typically eth0, eth1,...)
3. open the Networking-tool (System / Administration / Networking) and activate your device (if it isn't). Then click configure, fill in the details (SSID, WEP-key, etc).
4. don't forget to confirm your actions by clicking OK

See if it works now... if it doesn't, that's where my input comes to an end and we'll both need support from a more experienced user. :-)

Or... dig in the fora once more...

Good luck!



Roelski

---

