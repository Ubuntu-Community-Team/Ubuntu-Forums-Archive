---
title: "how to setup network connection"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-04-21
Hi 
   i have connected my ubuntu machine to my xp machine via a crossover cable. it is comming up on my xp saying that a local connection cable is plugged in etc but how do i go about setting it up on ubuntu. Thanks in advance

---

### Post by lingnoi on 2007-04-21
Could explain in more detail exactly what you are trying to do? 

Setup an internet connection from Ubuntu through to XP or XP to Ubuntu?

---

### Post by Dark-Angel on 2007-04-21
well i have the internet on my xp and want to get it on ubuntu. i have connected the two computers via crossover cable.

---

### Post by wormser on 2007-04-21
> **Dark-Angel said:**
> well i have the internet on my xp and want to get it on ubuntu. i have connected the two computers via crossover cable.

You need to set up internet connection sharing on the XP box.

[http://www.practicallynetworked.com/sharing/xp_ics/](http://www.practicallynetworked.com/sharing/xp_ics/)

---

### Post by Dark-Angel on 2007-04-21
well i have my xp machine connected to my router wirelessly so i thought it would already be set up for sharing.

---

### Post by wormser on 2007-04-21
Read that link I gave you.  Having your computer hooked up wireless is different from having your computer share its connection.

---

### Post by Spartan.II.117 on 2007-04-21
If your setup does not work after following the previous instructions, try this:

to set up the linux box once you have set ypur xp box up, click system > administration > networking, then on the wired connection and configure, change the drop down box from dhcp to static and input in an ip address in the 192.168.1.xxx range (probably 192.168.1.2) enter your subnet (255.255.255.0) and enter the dns information from your XP machine.

---

### Post by johnny4north on 2007-04-21
wornster is correct and you may have to set the ubuntu[7.04] networkcard to automatic config[dhcp]  i maybe wrong:(   here - panel > system > aministation > network > wired connection > properties..

---

### Post by Spartan.II.117 on 2007-04-21
sorry, i probably should have read the page myself, i did not remember ics having a dhcp server.

---

### Post by fuzzybunny on 2007-06-17
OK I really hope someone can help with this!
I have set up the network in much the same way as the original posterDark-angel.
I have been using static IPs for them and the Feisty computer can see the XP shared folders.

Both machines can ping each other.

Alledgedly ICS is running, (is there any way to check for ICS specifically?)

However no matter what DNS info I put in, I can't get a web connection through firefox. :(

The XP connection is through a Huawei e220 USB modem on a vodafone 3G network...

If I try using DHCP nothing works anymore (no network connection)

if i use **sudo dhclient eth0** i get "**no DHCPOFFERS received**"

Any ideas on how I share this connection to my Ubuntu box?

---

### Post by Gimpy_Rob on 2007-06-17
I am genuinely afraid of windows ICS...  I have gotten it working before, but there may have been black magic involved.  I would seriously consider getting a router, and using ethernet port on the back of the modem...  Several advantages as well.

---

### Post by Spartan.II.117 on 2007-06-17
> **Gimpy_Rob said:**
> Several advantages as well.

Among them is the fact that you will not burn out your USB port...

---

### Post by fuzzybunny on 2007-06-18
> **Gimpy_Rob said:**
> I am genuinely afraid of windows ICS...  I have gotten it working before, but there may have been black magic involved.  I would seriously consider getting a router, and using ethernet port on the back of the modem...  Several advantages as well.

I would, but it does not have one, sadly....
hence the pain in the *** ICS crap.

I can't figure out how to set up gateways etc on the bloody XP thing without the "wizard"
and sadly the XP ICS wizard would appear to be Rincewind.

ideally I would like to have the Ubuntu computer doing the sharing, but it does not want to play with the modem at all... :-(

So if anyone can help me with my issues?

---

### Post by fuzzybunny on 2007-07-05
For reference I got this sorted very easily by canning the Microsoft stuff and using ccproxy to share the connection.

---

