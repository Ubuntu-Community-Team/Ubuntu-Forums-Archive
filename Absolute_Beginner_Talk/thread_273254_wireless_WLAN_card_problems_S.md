---
title: "wireless WLAN card problems :S"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by beilard on 2006-10-07
i just finished downloading ubuntu on my computer and i need to configure my wireless card.. the only problem is that it does NOT appear in my options .. i only have the modem , and something which i dont know that is named " ath0 " ... my wireless card is a DWL-G520 , i already tried to follow instructions by putting a certain command in the command line .. but i cant manage to make it work ... can someone help me ?

---

### Post by Frak on 2006-10-07
Did you try wlan0?

---

### Post by motstudios on 2006-10-07
open a terminal

iwlist

if ath0 shows an access point then do the following, if wlan0 shows an access point, change the following references from ath0 to wlan0

iwconfig ath0 essid routeressid
# put ur routers essid shown from iwlist in place of routeressid

dhclient ath0
# should get u connected

---

### Post by beilard on 2006-10-08
thank you ill try it now. i do not have a wlan0 that's why i was having a problem. :D 
lets see if it gets me connected hehe

---

### Post by beilard on 2006-10-08
# put ur routers essid shown from iwlist in place of routeressid

excuse me but what does that actually mean ? 
i know im a bit a n00b for certain terms :P

---

### Post by beilard on 2006-10-08
so i tried to do what u told me , i found out wut was the essid , but when i put in the first command : iwconfig ath0 essid routeressid , it says : 

error for wireless request "set Essid" (8B1A)
Set failed on device ath0; operation not permitted

---

### Post by motstudios on 2006-10-08
sorry, i was tired when i posted.. try using sudo b4 the commands...

like:
sudo iwconfig ath0 essid routeressid

if the stuff i said doesnt work, just hang in there, someone will know a solution. also feel free to message me on yahoo as katasuka or *gasp* msn at [email]efosb@hotmail.com[/email] or even aim at efosbj im usually on all those messengers most of the time.

---

### Post by beilard on 2006-10-08
ah.... not even the sudo trick works. ill try to reinstall ubuntu to see if it was some sort of "error"

---

