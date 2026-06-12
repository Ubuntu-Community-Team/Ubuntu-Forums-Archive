---
title: "modem"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-30
just got my new linksys modem/router, need help in getting this modem to work with my windows first of,
then need to get working with ubuntu linux, the first thing i did is to connect erthnet cable to computer then to the erthnet socket on the modem,then the phone line into the rj45 one end in to the modem the other into 
the fillter,all is ok, now i have been to this gate way thing and did all what it says,then when i try to click onto the symbal on the screen,nothing comes up apart from this message that i need to have a look at my connection or somthing,and yes the lights on the mosem are all lit up, and i have btbroadband, so what should i be doing, any help on this subject  thank you

---

### Post by thekiller on 2005-12-30
I would say restart the router first, and then plug the ethernet line into ur computer. And can u please supply the make and model of your linksys router. If i am not mistaken, linksys router IP is 192.168.0.1 ?

---

### Post by richard willacy on 2005-12-30
name of modem/router/ linksys/wag354g/2.4ghz/wireless-g/ adsl home gatway/802.11g
and no number came up like 192.168.1.1 and the modem does seem to be working but every time i click on to somthing it just says cant connect to that pageand shows you somthing about dialing and connection 
stuff

---

### Post by thekiller on 2005-12-30
[QUOTE=richard willacy] it just says cant connect to that pageand shows you somthing about dialing and connection 
stuff[/QUOTE]

FOR WINDOWS :
Go to Start -> Run and type [COLOR="Red"] cmd [/COLOR]and hit enter. Then on the pop up window type [COLOR="Red"]ipconfig[/COLOR] and see if you have been assigned an IP.

FOR UBUNTU:

Check if you have been assigned an IP by the router by looking at the output of [COLOR="Red"]ifconfig[/COLOR]. If not then just do this :

```

sudo dhclient3 eth0

```

You will see some lines outputted on the screen and hopefully it should work.

(Assuming your ethernet device is [COLOR="Red"]eth0[/COLOR])

Then just type [COLOR="Red"]ping yahoo.com[/COLOR] to see if you are indeed connected.

---

### Post by richard willacy on 2005-12-30
i did what you say and this is what i get,ip address, 192.168.238.238/submask. 255.255.255.0
then when i went into the linux and typed sudo dhclient3, loads came up this is what it says
erthnet adapter local eara connection 2 dhcp v3.0.2,
and did type ping yarhh.com but nothing happend, i think i typed in the rong place

---

### Post by thekiller on 2005-12-30
[QUOTE=richard willacy]i did what you say and this is what i get,ip address, 192.168.238.238/submask. 255.255.255.0
then when i went into the linux and typed sudo dhclient3, loads came up this is what it says
erthnet adapter local eara connection 2 dhcp v3.0.2,
and did type ping yarhh.com but nothing happend, i think i typed in the rong place[/QUOTE]


Okay, if you are still on linux, then please run the dhclient3 command again, and paste the output here. If you are on windows, then go to the router's page (192.168.1.1) and make sure you did everything correctly. Try to remove the router for once, and connect your computer directly to the interent and see if it works. If it does work that way, then probably you didnt set up the router correctly.

---

### Post by richard willacy on 2005-12-30
disabled the wireless thing but still cant work this modem with windows or linux, when i try to go out in linux
it goes through this trying to connect thing, and the thing is it knows the moden is there and it is working
but i cant get out,its just a matter of time

---

### Post by richard willacy on 2005-12-30
what do you mean ping when setting up modem, and can sombody help me in
setting up so i can go out onto the web:confused:

---

