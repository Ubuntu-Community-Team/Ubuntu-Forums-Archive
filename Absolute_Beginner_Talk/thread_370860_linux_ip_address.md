---
title: "linux ip address"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by laychie on 2007-02-26
ok, i am lost when it comes to ip address, i mean what is it really? what's it purpose and is it  bad if someone finds out what my ip address is? 

and most importantly, can i change my ubuntu ip address? and i have my  windows already installed when i installed ubuntu so is my linux ip address the same with my windows'? thanks.

---

### Post by halitech on 2007-02-26
An IP address is the numeric representation of where your computer "lives" on the internet. If you have an insecure system, then yes it could be very bad if someone finds out your ip. 

As far as changing your ip, that will depend on your ISP and how they have you set up. If you have a statis ip then only your ISP can change it. If you have a dynamic, then restarting your computer (in theory) will get you a different IP. If you have a router, then your computers IP is safe due to most routers giving a non routable IP to client computers.

---

### Post by chewearn on 2007-02-26
> **laychie said:**
> ok, i am lost when it comes to ip address, i mean what is it really? what's it purpose and is it  bad if someone finds out what my ip address is? 


Simplistic explanation:
Analogy to real world, IP address is like your home address.  In order to send/receive information on the internet, your PC need to have an address for other PC and server to find you; just like the way a postman can deliver a letter to your home.

But unlike real world where the address is (mostly) fixed, IP address can change.  There is different network protocols/services that handle the changes, keep track of who is who, etc.


> and most importantly, can i change my ubuntu ip address? and i have my  windows already installed when i installed ubuntu so is my linux ip address the same with my windows'? thanks.

If you have a network at home with a router/gateway to the internet, the outside world sees you router IP address.  This IP is usually assigned by your ISP.  Inside your network, you need to have unique IP address for each connected devices.  For a simple home network, we usually use 192.168.0.xxx or 192.168.1.xxx as the format for IP addresses (xxx is a number from 1 to 254).  The subnet mask 255.255.255.0 is used to indicate that the last digit is unique, while the first 3 digits are the same.

---

### Post by bodhi.zazen on 2007-02-26
Think of your IP address as a phone number.

You are most likely using dhcp, a network protocol to set your IP address automatically. dhcp detects your MAC (serial number) of your network card and not your OS.

So your IP address may remain the same as you boot windows or Ubuntu on your computer because you are using the same network card with the same MAC on both OS.

AS has been pointed out, however, your IP address may change over time.

To see your actual IP address go here :

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

The first page will show you your external IP address, assigned via your IP provider ...

Click the "proceed" button on the bottom of the page ...

This will show you some info on security.

compare windows to ubutnu (log on to the site with both OS and test) ;)

---

### Post by OffHand on 2007-02-26
Think of it as your postal code and house number. With those details the postman is able to deliver a package at your house. Same goes for your IP address and the internet.

---

### Post by laychie on 2007-02-27
thanks guys. i'll keep it all in mind. i am interested more in learning networking. your explanations makes perfect sense to it all. now i get it! :)

---

