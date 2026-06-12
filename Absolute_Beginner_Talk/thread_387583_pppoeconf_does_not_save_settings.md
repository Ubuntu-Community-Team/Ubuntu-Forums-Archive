---
title: "pppoeconf does not save settings"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by SamYoung on 2007-03-18
To connect to the internet
I have to run pppoeconf every time I boot up , and then 
 ifconfig eth0 down, and ifconfig eth0 up.

What would be stopping pppoeconf from starting the connection automatically every time?


Thanks for any help, 

Sam


Edgy Eft, AMD64

---

### Post by zvacet on 2007-03-18
You can connect by typing
```
pon dsl-provider
```
but that is not what you want.system>administration>network setting>highlight your modem>properties>select type of connection you want>chek upper left box>close
Click on DNS and you will see one address and replace it with your nameservers>close
```
pppoeconf
```

---

### Post by chinocracy on 2008-03-01
Hi, I have the same problem as Sam Young. I have to do pppoeconf everytime, because after each boot, 'pon dsl-provider' and its sudo version don't work... the connection settings seem to have been lost! 

Here is the code of a 'pon' session I tried after booting, which did not connect:

```
chinocracy@chinocracy-desktop:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
chinocracy@chinocracy-desktop:~$ plog
chinocracy@chinocracy-desktop:~$ pff dsl-provider
bash: pff: command not found
chinocracy@chinocracy-desktop:~$ poff dsl-provider
/usr/bin/poff: No pppd is running.  None stopped.
chinocracy@chinocracy-desktop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
chinocracy@chinocracy-desktop:~$ plog
Mar  2 12:16:43 localhost pppd[8829]: Plugin rp-pppoe.so loaded.
Mar  2 12:16:43 localhost pppd[8831]: pppd 2.4.4b1 started by root, uid 0
Mar  2 12:16:43 localhost pppd[8831]: sendPacket: send: Network is down
Mar  2 12:16:43 localhost pppd[8831]: Exit.
chinocracy@chinocracy-desktop:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
chinocracy@chinocracy-desktop:~$

```

What could be preventing the previous pppoeconf from working in the next session? Thanks.

---

