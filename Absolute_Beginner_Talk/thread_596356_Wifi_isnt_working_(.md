---
title: "Wifi isnt working :("
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-29
My internet on my laptop suddenly stoped working today and i dont know why it says that its all connected and i can view my router configuration but cant view any webpages:confused: ive tried the live cd and another laptop and they work fine 

so has anyone got any ideas? thanx in advance:lolflag:

Im using kubuntu 7.4

---

### Post by cube3x3 on 2007-10-29
It may have mees up with ur DNS settings
Did u tried the 'ping [www.google.com](www.google.com)'  ? if its working, problem may be in firefox...

Write the 'nm-tool' in command-line and check the IP-settings when you are connected to your router. If it doesn't show any Gatway IP then you have to reconfigure your networking settings.

---

### Post by kamitsukai on 2007-10-29
right ok i tried what you said and well...lol hes what i have got

_"Ping www.google.com"_
```
Carl@islandmassive:~$ ping www.google.com
Ping: unkown host www.google.com
```

_"nm-tool"_
And i do have a default gateway 

and i cant load webpages in either firefox or konquerur but i have recentley unistalled guarddog firewall because i could'nt configure it properley but everything worked fine afterwards? could this be due to changes that guard dog made to the iptables?

---

