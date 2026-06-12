---
title: "internet connection with iburst modem"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by aeby on 2007-03-26
hi

i am using iburst (isp) modem, it is an usb modem, but i think you can connect it via ethernet cable , it is an ADSL modem i think so, and the guys have provided me with the  username and password can you please tell me how to connect to the internet with this  specifications, please let me know if you need additional details

thanks in advance

---

### Post by seshomaru samma on 2007-03-26
try this:
open a terminal (applications >accessories>terminal) and paste this command:
```
sudo adsl-setup 
```

after you configure it then go:
```
adsl-start
```

if this doesnt work then:


```
sudo pppoeconf
```

---

### Post by aeby on 2007-03-29
hi 


thankyou  for replying but i am not able to find the command adsl-setup and adsl-start  should i install any addittional pacakges if so can you please tell me.


Thanks in advance 
arsha

---

### Post by MoHamm on 2007-04-01
I am using iburst pcmcia, it is not usb but this howto helped me configure it, it might be useful.
 or you could probably send a message to Skrewdriver about the usb version

[iburst]("http://ubuntuforums.org/showthread.php?t=305020&highlight=screwdriver+iburst")

---

