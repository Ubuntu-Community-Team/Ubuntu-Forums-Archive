---
title: "ssh -- connection timed out error"
date: 2012-01-29
forum: Any Other OS
---

### Post by r3bol on 2012-01-29
Hi, I've been trying to set up a sftp connection to my n810 tablet (running openssh on maemo linux) so I can connect to it from my ubuntu laptop. The tablet is connected to internet through wifi. 

I've installed the client on the laptop, opened port 22 for the n810 on my router and started the ssh server. I've managed to login to the n810 through the openssh client on the n810 like this...
```
ssh user@user.dyndns.org
```
...but when I try it from another computer, I get this...
```
ssh: connect to host user.dyndns.org port 22: Connection timed out
```

Anyone have any idea why this might be?

Thanks

---

### Post by ajgreeny on 2012-01-29
If both machines are connected to the same router and you are connecting locally, do you really need dyndns.org?

When I use ssh between two linux machines I simply use ```
ssh user@192.168.0.#
``` the # varying with the particular machine.  All my machines have static IPs by reserving their addresses in the router configuration, and I don't need to specifically open any port in the router or firewall.  It would not be 2port 2 anyway, as I have changed that for slight added security.

Try the simpler command and see if it works.

---

### Post by r3bol on 2012-01-30
> **ajgreeny said:**
> If both machines are connected to the same router and you are connecting locally, do you really need dyndns.org?

When I use ssh between two linux machines I simply use ```
ssh user@192.168.0.#
``` the # varying with the particular machine.  All my machines have static IPs by reserving their addresses in the router configuration, and I don't need to specifically open any port in the router or firewall.  It would not be 2port 2 anyway, as I have changed that for slight added security.

Try the simpler command and see if it works.

I've just tried the tablet's local address and got the same error. 

The reason I want to get it working with the dynamic dns address, is because I want to have access to it when I am outside my LAN.

Edit: I've just discovered my ssh port was in stealthy mode. I'm researching whether that might be the problem now.

---

