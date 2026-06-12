---
title: "Can't access the internet.Help."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by joemacnz on 2006-09-24
G,day all,
          I have just managed to install ubuntu for the first time yesterday.However, I am having a little trouble getting online.The computer only has ubuntu on it and I have this one running windows. I have a D-LINK G604T wireless router but I am trying to connect using the ethernet option as that comp has no wireless card(yet...) Anyhow, I did 

sudo pppoeconf

And it came up with "sorry,I scanned 1 interface, but the access concentrator of your network did not respond.Please check your network and modem cables.Another reason for the scan failure may also be another running pppoe process which controlls the modem"

Can anyone tell me what this means and what to do about it?
The cables seem fine and all the relavent lights are going.My windows comp is running fine off the router(although using wireless)
Thank you

---

### Post by whizbaby on 2006-09-24
> **joemacnz said:**
>  "sorry,I scanned 1 interface, but the access concentrator of your network did not respond.Please check your network and modem cables.Another reason for the scan failure may also be another running pppoe process which controlls the modem"

Basically it's saying 'no contact to dsl-router'. To look for and kill a process:
**ps aux|grep pppoe**    (remember the first number(s) in the line(s), it's the process id)
**sudo kill -9 process_id_remembered**
Also try precising the interface
[B]sudo pppoeconf eth0
[/B]
If it doesnt help, setup ethernet manually (let's say IP 192.168.10.129):
**sudo ifconfig eth0 192.168.10.129 up**
and try to ping your router
**ping *REPLACE_BY_IP_ADRESS_OF_ROUTER***

---

### Post by joemacnz on 2006-09-24
Um I did all that.I think. Something has changed but I still can't get online.

I did a ping to my router (10.1.1.1) and that was all fine.(Q. how do you stop a ping?)

I used   "pon dsl-provider"
and got   "plugin rp-pppoe.so loaded"

Where to from here please?

---

### Post by whizbaby on 2006-09-24
> **joemacnz said:**
> Um I did all that.I think.
Be sure
> 
(Q. how do you stop a ping?)

Just like you stop any process running in terminal: *ctrl-c*
> 
I used   "pon dsl-provider"
and got   "plugin rp-pppoe.so loaded"

Where to from here please?
so I guess
ping [www.ubuntuforums.org](www.ubuntuforums.org)
does say *unreachable*? Is your router properly congigured to route the ethernet out?

---

### Post by joemacnz on 2006-09-24
Okay, the ping to ubuntuforums was all good "0% packet loss" I tried [www.trademe.co.nz](www.trademe.co.nz) which was pretty okay "7% packet loss"
Ok woooooooooohooooooooooooooo. I am online!thankyou thank you!!!:D

---

