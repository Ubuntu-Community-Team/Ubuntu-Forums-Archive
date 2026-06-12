---
title: "Very Strange Wireless Connection Working Wired is not detected"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by startgame412 on 2007-10-22
Hi, I am having a ratehr weird problem since upgraded ot ubuntu 7.10. My wired  Internet connection does not seem to be detected at all but my wireless for some reason or another is detectged out of the box and up and runnikng in ubuntu 7.10 which was not the case in ubuntu 7.04. How can I use and make the wired connection avialble for use?  I am using ubuntu on my playsation 3 but don't know the exact specs for it. Thanks.

---

### Post by RomeReactor on 2007-10-22
Hi. Try going to "System->Administration->Network" and see if your wired connection is disabled there. If it is, enable it and see if it works now.

Do you have Firestarter installed? if so, open it and go to "Edit->Preferences->Network Settings" and change the **Internet connected network device** form **wlan0** (or your correct wireless card designation) to **eth0**.

Note that doing this will  most probably disable your wireless connection.

---

### Post by startgame412 on 2007-10-22
Hi Wired connection is not even listed when i go to system administrater network.  Going to install firestarter and see if I can get something working there. Thanks.

---

### Post by startgame412 on 2007-10-22
wlan does not show up in firestarter only eth0 shows up even though it is being used as wireless as there is no wired network option in network under system administrater. What could be wrong that the wired connection is not being detected? With the wireless disabled, the light on the modem turns on to signify that it is indeed connected but there is no wired connection in network under system administrater. How do I fix this. Thanks.

---

### Post by startgame412 on 2007-10-22
Can anyone help? Anyone know anything about this odd  problem? Thanks.

---

