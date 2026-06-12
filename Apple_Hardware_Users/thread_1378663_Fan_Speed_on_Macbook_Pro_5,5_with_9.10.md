---
title: "Fan Speed on Macbook Pro 5,5 with 9.10"
date: 2010-01-11
forum: Apple Hardware Users
---

### Post by djpeterhenry on 2010-01-11
My first post!

This forum got me part way towards solving the problem of my Macbook Pro 5,5 running far too hot on 9.10 karmic koala.

I can set my fan speed with the command:

sudo sh -c "echo 5000 > /sys/devices/platform/applesmc.768/fan1_min"

for example, and putting the command:

echo 5000 > /sys/devices/platform/applesmc.768/fan1_min

in /etc/rc.local sets my speed appropriately at boot.  However, I have two questions:

1)  When I suspend / resume the fan speed defaults back to 2000 which causes the machine to run far too hot (I don't have exact temps, but it's hot!).  How can I solve this automatically so I don't have to remember to type the sudo command?

2)  Many posts refer to both ".../fan1_min" and ".../fan2_min", but my machine doesn't have a fan2_min.  Is this a hardware issue with the 5,5 Macbook Pro?  Otherwise, ideas on how I can see and control fan2 as well?

Thanks a bunch!

---

### Post by felipe51 on 2010-01-12
Your problems is probably related to fan speed and cpu frequency scaling

> Sensors (temps & fans)

Edit /etc/modules:

gksudo gedit /etc/modules

And add to the end:

coretemp

To enable temperature sensors. 
I had the same Overheating problem when my MacBookPro was actually not doing the cpu frequency scaling. The laptop was just in "*performance*" mode for some reason. I remember that it just began to happen when I did an upgrade to (karmic) and the second time when I tried to compile my kernel after a fresh install of (karmic) during the first days of setting it up.

Finally I ended installing a fresh (karmic), and skipped the compilation, so far its working fine by now.

best regards,
Felipe

---

