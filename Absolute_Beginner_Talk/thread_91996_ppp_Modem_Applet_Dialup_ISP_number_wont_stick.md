---
title: "ppp Modem Applet: Dialup ISP number wont stick"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by dalani on 2005-11-18
I have Ubuntu 5.04 intalled and running and set it up to connect to my ISP dial-up conection using the Gnome Modem Monitor Applet. 

But recently, for some reason, the dial-up service phone number disappears from the modem applet properties!! Any attempt to to type in the dial-up phome# into the field results in the same thing: upon closing the applet setup, the number disappears again.

I tried using the network tool in the adminstration menu as root,  and the same thing happens. The only to connect is to manually pu tin the number then activate the ppp connection without closing the Modem Monitor set-up.

Ideally I would like to automatically connect when I startup my browser. 

Hint: I had installed and run Firestarter firewall recently. I don't if that is related because it ran fine with Firestarter up and running.

---

### Post by towsonu2003 on 2005-11-24
if you feel like trying an alternative (bc I dont use the gui for dialup):

```
sudo wvdialconf /etc/wvdial.conf
``` and pray that it will detect the modem :) then ```
 sudo gedit /etc/wvdial.conf
``` and put in your ISP infoin required 'fields' and password too... save and close then ```
sudo wvdial
``` will dial... dont close the terminal and when you're done, go to wvdial running terminal and CTRL+C. if it's not dialing, try putting ```
Stupid Mode = yes
``` at the and of /etc/wvdial.conf file...

hope you'll like it...

---

