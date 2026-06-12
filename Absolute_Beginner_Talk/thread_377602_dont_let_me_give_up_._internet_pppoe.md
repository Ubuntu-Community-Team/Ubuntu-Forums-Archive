---
title: "dont let me give up . internet pppoe"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-06
im looking for the guide that explain how to connect through pppoe . 
im asking for help for a few days and find no answer at all. i saw many post for the same problem i have - the connection failed after few minutes or doesnt connect at all. 
i did all the sudo pppoeonf process at the first i was surfing but then the connection failed . 
i really need some help here . i dont want to give up on ubuntu , i like the concept of linux, and i cant stand microsoft .. remember im totally new in the buisness , and english isnt my first language.

Thanks ahead!

---

### Post by marko_4454 on 2007-03-06
I have been having problems as well....this is what worked for me:
you should try adding these DNS servers:

208.67.222.222
208.67.220.220

This is done by: System >> Administration >>Networking>>DNS tab
and start adding them.
These DNS servers are for something called OpenDNS which is explained further here:
[http://www.opendns.com](http://www.opendns.com)

You should also try to disable IPv6 which normally just causes more problems.

---

### Post by fanny on 2007-03-06
i tried it . still no solution. i saw the guide [http://ubuntuforums.org/showthread.php?t=239815](http://ubuntuforums.org/showthread.php?t=239815)
but for the first step i need to do :"apt-get install build essential". i did it but it was imposible probably because i supposed to be connected first? so what the point?

---

### Post by marko_4454 on 2007-03-06
yea, that doesnt help...
You must have a router or modem right? Can you connect to it via IP?
If you dont know your IP, just look for it online.
These are a couple of possibilities:
192.168.1.1
192.168.1.254
192.168.0.1

---

### Post by fanny on 2007-03-06
i did it already it didnt work also. until now only once i had success see the browser work.

---

### Post by marko_4454 on 2007-03-06
ok, I am running out of ideas...but lets see.
1) Are you running DHCP? If not, test if it works with DHCP instead of static.
2) Can you ping anything at all? 
3) Maybe a stupid question, but do you have your username/password correct?

---

### Post by fanny on 2007-03-06
what is dhcp? 
yes my pass and user name are correct .
i cant ping at all.

---

### Post by marko_4454 on 2007-03-06
DHCP just means that your router/modem provides the IPs for you, instead of you selecting them. Somehow for me that caused a problem.
Just go to Sytem>>Administration>>Networking and look at your ethernet controllers...it should tell you there "Address: DHCP". If not, then select it, and click properties. It the tick in "Enabled" should be there. In "Configuration" change it to DHCP.
Also what service are you using? and what router/modem are you using?

---

### Post by fanny on 2007-03-06
im using a 1.5 mega internet adsl with modem tnn 600e.

---

### Post by meborc on 2007-03-06
edit: never mind... just read your first post :)

---

### Post by marko_4454 on 2007-03-06
so I am assumming DHCP didnt work...
did you try it ? or was it already DHCP?

Also, go to your browser and try this IP: 10.0.0.138
Do you get something? anything at all? 
If you dont, then that means that you dont even have communication with your modem which is not good. That means that ubuntu is screwed up. 

Just for reference about your modem::
[http://www.petri.co.il/forums/showthread.php?t=4509](http://www.petri.co.il/forums/showthread.php?t=4509)

---

