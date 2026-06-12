---
title: "Connecting to internet using Ethernet"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by milad on 2006-11-02
First, let me say that i am a total newbie to Linux.

I have both Windows XP and Ubuntu 6.0.6 installed on two seperate hard drives and i can connect to internet using my ethernet modem in windows without  any problem, i simply plug it in and that's it. I thought it would be the same in linux but when i tried firefox and it couldn't connect to internet. 
I think Ubuntu detects my ethernet modem properly because when i go to network tools i can even see my IP address. So instead of using DHCP i tried ipconfig in windows command prompt, wrote down ip, subnet mask and gateway and entered them manually in ubuntu and the problem was solved.

(i entered 255.0.0.0 instead of 255.255.255.0 in subnet mask field)

anyways, as my isp assigns differrent IPs from time to time, i want to know if  there is anyway i can get DHCP to work ..

Can anybody help me?

---

### Post by dbott67 on 2006-11-02
The comparable commands for Ubuntu are:

To look at all current interface settings:
```
ifconfig -a
```

To disable the interface:
```
sudo ifdown eth0
```
 
To enable the interface:
```
sudo ifup eth0
``` 

To obtain IP address:
```
sudo dhclient eth0
```

Just replace 'eth0' with the appropriate interface obtained from **ifconfig -a**.

-Dave

---

### Post by EdThaSlayer on 2006-11-02
In Ubuntu to have your IP changed to DHCP just go to System->Administration->Networking->click on the ethernet icon->Properties->Configuration->change configuration to DHCP

Hope this helps you!
Welcome to the world of Linux!

---

### Post by dbott67 on 2006-11-02
Set your network settings back to DHCP.  If you have trouble connecting to the internet after booting into Ubuntu, try performing these steps (I'll assume that your interface is 'eth0'):
1. sudo ifdown eth0
2. sudo ifup eth0
3. sudo dhclient eth0

Post the output of each command here if you're still having troubles.

Also, if you could provide the following:
- internet connection type (DSL, cable, etc.)
- connected to router (D-Link, Linksys, Netgear) or direct to modem.

Thanks,
Dave

---

### Post by colby500 on 2006-11-07
I had a similar problem and dbott67's instructions worked like a charm.

Thankyou guys!

---

