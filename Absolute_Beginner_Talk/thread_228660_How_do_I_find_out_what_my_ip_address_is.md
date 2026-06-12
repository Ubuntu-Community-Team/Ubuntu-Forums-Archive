---
title: "How do I find out what my ip address is?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Sammi on 2006-08-03
How do I find out what my ip address is?

---

### Post by kinematic on 2006-08-03
sudo ifconfig

---

### Post by firebadger on 2006-08-03
type:
ifconfig

---

### Post by cstudent on 2006-08-03
That gives the local network ip but not your external ip. For me anyway. My machines sit behind a DSL router/modem and all I see is the local ip. To find your external ip address

[http://www.whatismyip.com](http://www.whatismyip.com)

or my favorite

[http://www.ipchicken.com](http://www.ipchicken.com)

---

### Post by slakkie on 2006-08-03
ifconfig -a

Their is NO need use sudo for these kind of commands. You do not need root permissions to see your configuration. Only use sudo when you want to change your interface config.

---

### Post by Sammi on 2006-08-03
Right. Thanks.

As cstudent states, those only give me my local network ip address, and those websites work fine, but is there no command that can give me my external ip?

---

### Post by slakkie on 2006-08-03
No - you cannot execute a command that will show you your IP address of your ISP. You need to get this from your DSL modem/router or from an external source such as the websites posted.

On a "normal" system the IP configured on any of the interfaces is most likely to be the public IP address:
```

eth0      Link encap:Ethernet  HWaddr 00:12:79:C2:BF:14
          inet addr:194.134.32.247  Bcast:194.134.32.255   
          Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

If you would use a dialup connection you would see with `ifconfig -a` the IP address given to you by the DHCP server and you would not see a private (internal) IP range. 

Your PC is part of your own internal network, which has its own private IP space. Your DSL modem knows its IP address on the public interface and also has an IP address on the interface which is connected to your network (and often this will be your PC).

Conclusion:
If you want to see your IP address from your ISP, check your DSL modem/router or visit one of the websites mentioned earlier.

---

### Post by az on 2006-08-03
There are some tools for some specific routers which will give you your ip address.  For things like dynamic dns, most routers have dyndns clients built-in.

---

### Post by thinsoldier on 2008-04-02
Where in the system preferences/administration can I see my IP Address?

---

### Post by ofb on 2008-04-06
System > Administration > Network Tools

---

### Post by 4nsitian on 2008-04-06
Go in system menu------->network---------->here you need to enter your root password.
after then you need to select your networking interface that is eth0 or eth1 or otherwise. select the edit tab and there you can see your networking configuration

---

### Post by wolfvorkian1 on 2008-04-06
> **Sammi said:**
> How do I find out what my ip address is?


Paste this in a terminal for your external IP. I made sort of a macro for it using a program called xclip. 

wget -qO - [http://myip.dk/](http://myip.dk/) | egrep -m1 -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'

---

### Post by jakupl on 2008-04-06
thanks wolfvorkian1 :)

---

### Post by Ripfox on 2008-04-06
> **wolfvorkian1 said:**
> Paste this in a terminal for your external IP. I made sort of a macro for it using a program called xclip. 

wget -qO - [http://myip.dk/](http://myip.dk/) | egrep -m1 -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'

Niiice.

---

### Post by ofb on 2008-04-07
> **4nsitian said:**
> Go in system menu------->network---------->here you need to enter your root password.
after then you need to select your networking interface that is eth0 or eth1 or otherwise. select the edit tab and there you can see your networking configuration

That doesn't work if the device is in Roaming Mode, which is default now. Hence use "System > Administration > Network Tools" to get around that little hiccup.

... and since this is the AB forum, I should have been more specific and added: go to Devices panel, and select Network Device eth0 (possibly eth1 if you use two cards) to view IP address.

Note that most internet service is DHCP these days, so your IP may be different next session.

---

### Post by Saverio on 2008-04-29
Try the two scripts I wrote:

[http://saverio.bolognani.googlepages.com/backupinlinux2]("http://saverio.bolognani.googlepages.com/backupinlinux2")

they return both you LOCAL and "EXTERNAL" ip address.

Hope it helps!
Ciao, 
 Saverio

---

### Post by orangesss on 2008-07-11
Hello! I found excellent site on determination of ip. [ lookup ip service ]("http://smart-ip.net/en/")

---

### Post by bobbob1016 on 2008-07-11
ipchicken.com

---

### Post by mega1 on 2008-07-20
You can see it upon entering such sites that can show you your ip.

[here is your ip](http://smart-ip.net/en/) :)

And sometimes they also show where we are living on a map.)

---

