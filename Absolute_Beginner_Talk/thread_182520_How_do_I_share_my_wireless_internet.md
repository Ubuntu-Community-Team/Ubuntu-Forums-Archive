---
title: "How do I share my wireless internet?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-26
I have managed to install and configure my wireless device. I am now faced with another task-that of sharing my connxn via LAN so i act as a gateway to other comps. How is this done in Ubuntu?

---

### Post by tkjacobsen on 2006-05-26
maybe this howto can help you:
[http://ubuntuforums.org/showthread.php?t=91370&highlight=howto+share+internet](http://ubuntuforums.org/showthread.php?t=91370&highlight=howto+share+internet)

---

### Post by Robgould on 2006-05-26
You don't have to do anything.  Just let it broadcast.  People will be able to detect it and connect at will.  If you want to secure your connection with a WEP key, you can, but then you would have to provide that key to people you want to be able to use it.  

All a user has to do is go to system->administration->networking and configure their ath0 connection.
  
Highlight the connection then choose properties.  Click the down arrow in the netowrk name box, select the appropriate access point, configure the other settings there and then click ok.  

Back at the main screen click activate.

Done.

---

### Post by Koech on 2006-05-26
I meant sharing it out once I receive ie via LAN, as a gateway to the rest of the comps on LAN. Is ther a way I can restrict it too?

---

### Post by Robgould on 2006-05-26
You restrict it by using a WEP key.  You cannot just restrict it to your LAN.  It will broadcast and that broadcast can be picked up by anyone in range.

You have to add the setting to the connecting computer.  The access point then handles all LAN gateway stuff on it's end.

---

