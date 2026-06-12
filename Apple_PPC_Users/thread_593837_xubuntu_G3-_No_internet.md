---
title: "xubuntu G3- No internet"
date: 2007-10-27
forum: Apple PPC Users
---

### Post by iAtari on 2007-10-27
I recently installed xubuntu 6.06 on a 233Mhz Tray iMac G3. Installed fine, booted fine. 

Problem: No internet. The Network Manager says that the Ethernet connection is active, My router gets a signal but doesn't appear to be delivering any data through the cat 6 cable. Firefox won't load any webpages, as there is no internet connection. The guides inside Firefox instructing me how to set up the connection using terminal gave me a message:

Connection failed

I'm not sure what to do-i set up the network inside the installer. Still no result.

Any suggestions?

thanks,

iAtari

---

### Post by xelapond on 2007-10-29
Try ifconfig in a terminal and paste back the results.

Alex

---

### Post by iAtari on 2007-10-29
I get addresses and a location under eth0. Looks to have all data with no errors. i've read that eth0 is ethernet, and in the network manager it says i'm connected.

Its just firefox at this point.

---

### Post by iAtari on 2007-10-29
Ok. here's my current situation:

When installing the opera browser, i noticed that the install package was using the internet to download an update, therefore the modem is connecting and working on xubuntu.

Even so, Gaim, Firefox and Opera don't find the connection.

Any help?

Thanks,

Adam

---

### Post by xelapond on 2007-10-31
Yes, Please paste your output of ifconfig so I can look at it.

Also try installing an application in terminal like googleearth-package.  The code is:

sudo apt-get install googleearth-package(or whatever other package you want to install).


~Alex

---

### Post by iAtari on 2007-11-01
Here's my ifconfig results:

[SIZE="1"]imac22@xumac:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:02:4B:B3:01
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:2ff:fe4b:b301/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17182 (16.7 KiB)  TX bytes:1990 (1.9 KiB)
          Interrupt:42 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1172 (1.1 KiB)  TX bytes:1172 (1.1 KiB)

imac22@xumac:~$[/SIZE]


I attempted the sudo apt installs with 5 different programs, all i've used on ubuntu before. 
No luck, says 

[SIZE="1"]imac22@xumac: sudoapt-get install amsn
password:
unloading: 100%
Error: Cannot get install amsn sudo.

imac22@xumac:[/SIZE]

So, any ideas?

thanks,

Adam

---

### Post by xelapond on 2007-11-02
Is the iMac going trougha  router? or directly from the modem?

Also, in your install applications command, you need a space between sudo and apt-get, so it ends up being:

```
 sudo apt-get install amsn
```

---

### Post by iAtari on 2007-11-02
Using a direct modem. 

Any tips?

~Adam

---

### Post by iAtari on 2007-11-03
I've reloaded (reinstalled) xubuntu 6.06 onto the iMac. 

Now, we have an active connection, only firefox displays "connection has timed out" messages. 

It is possibly the 64MB ram isn't enough to handle firefox...?

iAtari

---

### Post by xelapond on 2007-11-03
I don't know how much ram firefox takes.

Do other programs use the internet fine?

Try pinging ubuntu and see what happens

```
ping www.ubuntu.com
```

Alex

---

### Post by iAtari on 2007-11-03
No, Gaim disconnects from any account after attempting to connect for around 5 minutes, Opera just quites on startup. I think i'll attempt a lighter browser, such as epiphany or dillo. 

Results for the ping:

```

64 bytes from www.ubuntu.com (91.184.56.147) 2 icmp-seq=31 ttl=48 time=21
```

iAtari

---

### Post by xelapond on 2007-11-04
OK, if your ping returned that means that the internet is working.

Try some lighter browsers, maybe even lynx.

Alex

---

### Post by iAtari on 2007-11-05
I'm working on getting some CD-Rs and some CD-RWs, puts this project back a few days.

iAtari

---

### Post by iAtari on 2007-11-11
Epiphany works great, loads Apple website and Ubuntu website within 5 seconds. :)

Now its just onto installing a flash player, xubuntu isn't using an extractor... 

iAtari

---

### Post by iAtari on 2008-03-19
Anyone Reading this thread, I've long disabled IPv6 in firefox, as the iMac is connected directly to my router. Firefox now works. :^)

---

