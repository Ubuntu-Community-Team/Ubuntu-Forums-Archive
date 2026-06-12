---
title: "dialup problems"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by wildthing-zim on 2005-09-12
I have a HP/Compaq nx9030 , it has a internel AC97 modem , i have installed drivers from linuxant.com for this modem ,using minicom i have managed to do a dialup connection with /dev/modem 

with gnome ppp setting the modem to /dev/modem it says in the log :
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied

i go to the networking tool and disable ether0 and enable ppp0 and confirm ppp0 is using /dev/modem

can anybody shed some lightr as to where i am going wrong 

thanks

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=wildthing-zim]I have a HP/Compaq nx9030 , it has a internel AC97 modem , i have installed drivers from linuxant.com for this modem ,using minicom i have managed to do a dialup connection with /dev/modem 

with gnome ppp setting the modem to /dev/modem it says in the log :
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied
--> Cannot open /dev/modem: Permission denied

i go to the networking tool and disable ether0 and enable ppp0 and confirm ppp0 is using /dev/modem

can anybody shed some lightr as to where i am going wrong 

thanks[/QUOTE]
 Well, personally, I prefer using pppd to connect to the internet. 

I just run pppconfig to create a script (let's call it "ISP")

then I'd type:
sudo pppd file /etc/ppp/peers/ISP

For some reason though, I need to open up a browser (or something to use ppp) afterward for it to dial... it used to dial straight away at one point. Meh... it works for me!

---

### Post by wildthing-zim on 2005-09-12
nope that did not work for me at all.

i did see that there is a advanced option called demand dial , if that is enabled you must launch a browser to make it dial ....

try taking that off for your connction ..

me , i am still stuck , what really bugs me is that the drivers installed from linuxant.com will only work at 14400 as i have not paid for a licence so once i have it working there will have to be some way of getting rid of that .

---

### Post by Bruce3000 on 2005-09-12
Have you had a look at [www.linmodems.org](www.linmodems.org) ?

I dunno if they have source for your particular modem, but I managed to get a crappy old lucent winmodem working under Gentoo (for which there was no driver available at the time)...

Outside that, ATM all I can think of is chmod and chown :P

---

