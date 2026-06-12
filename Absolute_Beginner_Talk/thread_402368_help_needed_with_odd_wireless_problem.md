---
title: "help needed with odd wireless problem"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by rotarymike on 2007-04-05
info:
IBM thinkpad R52, Edgy 586 kerrnel with Gnome. 

wireless is the internal IBM A/B/G mini-pci card. 

Had wireless working from install (yay), went to friends house, had to put the ESSID in to make it connect to his network, then came home and it won't power on.

let me explain what I mean - there is an indicator LED on the laptop that shows when the wireless is broadcasting. In windows it behaves thus: light on, wireless on but not doing anything. Flickering, like a HD light: transferring data. Out: wireless disabled. In my case, the light is out.

Tried enabling the wireless (ATH0) under the network manager panel, and it says it's enabled... but it's still not on, and of course will not connect or get a dhcp return etc.

Is there some simple switch that should turn the hardware on?

-Mike

---

### Post by Hortinstein on 2007-04-05
you might wantto check your interfaces file in /usr/networking and see if your card is listed there...

thats the first idea that comes to my mind, since maybe he altered something

---

### Post by rotarymike on 2007-08-07
solution: reinstall with 7.04, solved problem. I also have no problems using the wireless now at friend's house (even though he's not broadcasting SSID).

?? Chalk this one as a win.

---

