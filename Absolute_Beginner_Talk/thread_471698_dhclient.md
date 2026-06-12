---
title: "dhclient"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Fakircho on 2007-06-12
Hello everyone 

I finally installed Ubuntu as the main operating system on one of my PC's.  
I have a issue connecting to the internet. My provider uses the physical address of my network card to grant me access. So once i have given that to my provider everything should work. 
The first time my internet connection was activated by my service provider Ubuntu connected to the internet without a problem. After a while however the connection was lost. 
I scratched around in the forums here and found a few threads that were relevant. 
Now every time i switch my computer on i have to call up the terminal and enter "sudo dhclient" in that resolves my problem and the internet works until the next time i shutdown or restart. 

What do i have to do to resolve this problem permanently and why is this happening? 

I am probably not giving enough info so please let me know what i need to provide. 

Thanks

---

### Post by gerscht on 2007-06-12
what does the output of your /etc/network/interfaces look like?
```

sudo less /etc/network/interfaces

```

---

### Post by lazyart on 2007-06-12
I would get a router that can "spoof" the hardware address.  You tell the router what address it is "supposed" to have and it will report that back to your provider.  This way when you change machines (or even NIC card for that matter) you don't have issues.

---

### Post by Fakircho on 2007-06-12
Thanks I will run 
sudo less /etc/network/interfaces 
and let you know what it gives me when i get home to my Ubuntu machine

---

### Post by Fakircho on 2007-06-12
lazyart , i do not what you mean. How i am i supposed to get a router that can "spoof" the hardware address?

---

### Post by freebeer on 2007-06-12
Most routers that I've seen have a feature that allows you to tell it what MAC address to use.  This is the "spoofing" part.  You're telling the router to use your network card's MAC address.  That way your ISP thinks it's seeing the network card that your account is set up to work on.  The router then does its job of routing the data packets to and from your machine(s).  The advantage to this arrangement is that you can hook up multiple machines to share your internet access, and you have a safer environment from hackers, etc.

---

### Post by Fakircho on 2007-06-12
Ok so i ran the 
sudo less /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0

---

### Post by Fakircho on 2007-06-12
Thanks Freebeer but i still do not know how to do that ? 

I am very new to this so i need an explanation if possible

---

### Post by freebeer on 2007-06-12
How to do it is dependant on the model of router that you have.  Do you have a router at this point?

---

### Post by Fakircho on 2007-06-12
Please read my original question. i do not have a router. I loose my internet connection 
every time i reboot or i shutdown my PC. So i have to open terminal and enter 
 
sudo dhclient 

the connection then works until the next time i reboot or shutdown

---

### Post by Fakircho on 2007-06-12
Can any offer any advice ?

---

### Post by Fakircho on 2007-06-13
Can anyone tell me what dhclient does? 
And why do i need to keep ruining this command in terminal for me to have internet access? 

When i boot up Firefox can not access anything. When i enter dhclient in the terminal everything works fine until the next restart or reboot.

---

### Post by pxwpxw on 2007-06-13
> **Fakircho said:**
> Can anyone tell me what dhclient does? 
And why do i need to keep ruining this command in terminal for me to have internet access? 

When i boot up Firefox can not access anything. When i enter dhclient in the terminal everything works fine until the next restart or reboot.

**Fakircho**

dhclient gets your internet address from a dhcp server. If you dont have a router, it probably gets the address from you ISP.

Go to the "**Networking & Wireless**" forum, and post a question there, you need help to set up

/etc/network/interfaces and maybe other files, to run dhclient automatically.

---

### Post by freebeer on 2007-06-13
> **Fakircho said:**
> Please read my original question. i do not have a router. I loose my internet connection 
every time i reboot or i shutdown my PC. So i have to open terminal and enter 
 
sudo dhclient 

the connection then works until the next time i reboot or shutdown


Oops.  Sorry.  I must have gotten you confused with a few other threads that did have to do with routers and port forwarding.  My bad.  :D

I don't use dhclient (or if I do, it was automatically set up on install).  Have you tried putting that commend in your startup folder?  (something/init.d I think)  Sorry.. I'm on a Windows machine right now and can't check.

---

### Post by Fakircho on 2007-06-13
Thank you guys for the replys :)

I will post this on the networking forums

---

