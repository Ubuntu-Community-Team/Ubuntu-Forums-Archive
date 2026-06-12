---
title: "Problem with Realtek RTL8019 PnP LANadapter"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by radames on 2006-03-06
Problem with Realtek RTL8019 PnP LANadapter

I have this ISA network card on my old computer and on ubuntu there is no card detected;what the solution may be to setup this card and to have an internet connection? Thanks for help! ;)

---

### Post by jamesr on 2006-03-07
I am not sure if the driver is part of the standard set, but try

sudo ifconfig -a
sudo modprobe RTL8019
sudo ifconfig -a

---

### Post by radames on 2006-03-07
it doesn't work:

radames@raluca:~$sudo modprobe RTL8019
FATAL: Module RTL8019 not found.
radames@raluca:~$

The question is: where may I find this module? or a .rpm driver to convert it to debian with "alien";

radames@raluca:~$alien -d file to convert ( example file.rpm )

Thanks for all answers! 
Radames

---

### Post by jamesr on 2006-03-07
with a bit googling the standard ne2000 driver will work
```
sudo ifconfig -a
sudo modprobe ne2000
sudo ifconfig -a
```

PS is any mention made of eth0 in dmesg

```
sudo dmesg |grep eth0

```

---

### Post by radames on 2006-03-07
Hello again!
Unfotunatelly, sudo modprobe ne2000 does not work....

[B]radames@raluca:~$ sudo ifconfig -a
Password:
lo
          Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:68806 (67.1 KiB)  TX bytes:68806 (67.1 KiB)
sit0      
          Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

radames@raluca:~$ sudo modprobe ne2000
FATAL: Module ne2000 not found.

radames@raluca:~$ sudo ifconfig -a
lo        
          Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:87828 (85.7 KiB)  TX bytes:87828 (85.7 KiB)
sit0      
          Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

radames@raluca:~$[/B]

So, i'm in a big dilemma. Any ideas ?

---

### Post by radames on 2006-03-07
[COLOR="Red"]Finally it's DONE[/COLOR]

SO:
i have to type next:

radames@raluca:~$ **sudo modprobe ne**

then i type:
radames@raluca:~$ **sudo ifconfig -a** , and i saw eth0 as first text block;

After that i did the next:

click on

System -> Administration -> Networking 
Appears the "Network settings" window;
In Connections Tab -> Select "Ethernet connection" -> Properties
On the new window I checked "Enable this connection"
I choose static IP address, then I filled up the spaces with necesary data;
Click OK
Click on DNS tab
Click Add and here I typed the 2 DNS what I have;
Click OK from the bottom of the window;
And, here it is.. the computer is responding at ping on it own IP; it's ping response from default gateway, and of course  is ping response from [www.yahoo.com](www.yahoo.com)

Thanks for help, jamesr, You just gave me a good suggestion with ne(2000)
Wish you all the best!

---

### Post by jamesr on 2006-03-07
You will need to edit the /etc/modules to add a line ne so that it installs the module automatically at subsequent  boots.

---

### Post by radames on 2006-03-08
Hello again!
Right, in this morning when i start the computer, i did not find the network card; I have to setup again. I don't know what to wrote in  /etc/modules.
Thanks for any sugestion which may help to improve the performance
Radames

---

### Post by dvarsam on 2006-03-08
I think that what "jamesr" suggested is to add/type JUST two letters in there:

ne

Hopefully that should work.

Tell us if that worked for you...

---

### Post by jamesr on 2006-03-08
```
sudo nano /etc/modules
```

Add a new line at the end containing

ne

save and exit.

If you are still having diffliculties post the output of 

```
cat /etc/modules
```

---

### Post by radames on 2006-03-08
Hello again!

I write just 
**ne** 
in a new line in /etc/modules, and at the new restart, the network card is enabled;

Thanks you all guys for your help!
Radames

---

