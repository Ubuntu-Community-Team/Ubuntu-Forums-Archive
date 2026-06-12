---
title: "Internet problems"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-09-29
I have an internet connection via Router
now, since i installed Ubuntu, my internet doesn't work on my Windows, but only on Ubuntu

any ideas?

---

### Post by por100pre1 on 2007-09-29
Type this in terminal:

```
ifconfig
```

Look for eth0. Write down in a piece of paper the MAC address shown right next to HWaddr, it should be something like this: 00:8C:42:78:36:B5

Login to Windows and verify that the MAC address of your Local Area Connection is the same. I suspect the router is confusing Windows and Ubuntu as two different computers.

---

### Post by lennartack on 2007-09-29
Did internet work on windows before you installed ubuntu? It's very strange that ubuntu causes windows internet to stop working...

If it's the mac address like por100pre1 said:
You can change the mac address with some program(not easy to do, so you'd better not try this), or you can add the mac address of your windows to the dhcp server of your router. So, from ubuntu, you need to go to the internet page of your router and find dhcp settings. Then add the mac address of your windows to the allowed mac addresses or something.

---

### Post by asakurax on 2007-09-29
my internet worked perfectly b4 i installed ubuntu
i checked the mac addesses - both are the same
but, there is something weird:
the properties of the internet connection
[http://img299.imageshack.us/img299/2816/99766922el4.jpg](http://img299.imageshack.us/img299/2816/99766922el4.jpg)

i have no idea where is IP address came from
my router IP address is 10.0.0.138
weird stuff.....

---

### Post by lennartack on 2007-09-29
> **asakurax said:**
> my internet worked perfectly b4 i installed ubuntu
i checked the mac addesses - both are the same
but, there is something weird:
the properties of the internet connection
[http://img299.imageshack.us/img299/2816/99766922el4.jpg](http://img299.imageshack.us/img299/2816/99766922el4.jpg)

i have no idea where is IP address came from
my router IP address is 10.0.0.138
weird stuff.....
Windows uses that ip when your router doesn't assign an ip address to your pc.

I really don't understand why your internet doesn't work on windows, but maybe someone else... Can you tell me how your internet is configured on ubuntu?

---

### Post by asakurax on 2007-09-29
> **lennartack said:**
> Windows uses that ip when your **router doesn't assign an ip address to your pc.**

I really don't understand why your internet doesn't work on windows, but maybe someone else... Can you tell me how your internet is configured on ubuntu?

how come it assigns an IP for Ubuntu and not for windows?

---

### Post by JBAlaska on 2007-09-29
Weird...but it should be easy to fix.
Check your working INTERNAL IP and DNS settings in ubuntu
Boot windoze and enter that IP and DNS manually in tcp/ip settings using your routers login IP as the gateway IP.

Better to have a static internal IP in winblows anyways

---

### Post by pbskid on 2007-09-29
I have the reciprocal of this problem. My DSL thingy works fine on my Windows computer but not on my Ubuntu computer. Any help?

---

### Post by JBAlaska on 2007-09-29
pbskid, try using your windoze numbers (IP and DNS), plug them into "manual configuration" in ubuntu...let it settle, then go back to dhcp in ubuntu, you should be connected then..I have to do this everytime I boot from a live CD for some reason.

---

### Post by lennartack on 2007-09-30
Do what he said:
> **JBAlaska said:**
> Check your working INTERNAL IP and DNS settings in ubuntu
Boot windoze and enter that IP and DNS manually in tcp/ip settings using your routers login IP as the gateway IP.

If you have feisty you can right click on the two pc's in the system tray and click connection information to find the information(default route is your router and is called gateway in windows).

If you have an older version of ubuntu you can check your ip with the command ifconfig, and your dns servers: cat /etc/resolv.conf.

---

### Post by asakurax on 2007-10-04
> **JBAlaska said:**
> Weird...but it should be easy to fix.
Check your working INTERNAL IP and DNS settings in ubuntu
Boot windoze and enter that IP and DNS manually in tcp/ip settings using your routers login IP as the gateway IP.

Better to have a static internal IP in winblows anyways

ok, ive entered all the internet setting manually to the windows configuration
now when i try to enable the network, i get a msg "IP conflict" something
its like there is a conflict between Ubuntu and Windows

---

### Post by clancymf on 2007-10-04
How do you have these set up? Dual Boot?

I dont know a whole lot about ubuntu but try this on your windows side:

go onto your command line (start>run>cmd) and type in:
 ipconfig /refresh
 ipconfig /renew
 ipconfig /all

See if that worked ( you should have an ip # of 10.something or a 192.something)
if you dont log into your router and see what the ip address, subnet mask, and gateway are setup to

then go back into windows and manually config your static ip address using a different number in the last octet.  for example if your gateway is 192.168.0.1 then make your static ip 192.168.0.9

Good luck

---

### Post by asakurax on 2007-10-11
well, the problem is that my router only give my MAC adreess a specific IP
now, when i try to manually insert that IP into windows network configuration, it gives the IP Conflict error

---

