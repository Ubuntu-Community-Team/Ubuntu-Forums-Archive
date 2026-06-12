---
title: "WEP seems to be configured right"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Bubs on 2007-03-08
I have looked at a lot of the different threads on wep and tried the fixes but I can't get online.

I'm using edgy eft 64bit

my "/etc/network/interfaces/ "  looks like this for my wireless card

```
auto ra0
iface ra0 inet dhcp
wireless-essid six21
wireless-key xxxxxxxxxx

```
and the network restart  goes to "DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4"
and keeps going through intervals intil it says "No DHCPOFFERS recieved" and "No working leases in persistant database - sleeping"

I think my problem is in the WEP because when I set up the router I tested all my wireless computers (2) to make sure that they worked before I tried the encryption.

and to make sure that the wireless key is right I have my laptop next to me (which is working, but with another distro) logged into the router with the key up on the screen.

suggestions please :)

---

### Post by shanepardue on 2007-03-09
You might want to try Network Manager. I believe the package is called 
"networkmanager" but I may be wrong..my apt is tied up at the moment.

Network Manager is what the new ubuntu (Feisty Fawn) uses by default and it's 
supreme in finding wireless networks even with encryption.

---

### Post by nanotube on 2007-03-09
> **shanepardue said:**
> You might want to try Network Manager. I believe the package is called 
"networkmanager" but I may be wrong..my apt is tied up at the moment.

Network Manager is what the new ubuntu (Feisty Fawn) uses by default and it's 
supreme in finding wireless networks even with encryption.

just a correction: package is "network-manager", and the one that actually installs the fancy gnome applet is "network-manager-gnome" :)

---

### Post by shanepardue on 2007-03-09
Thanks nanotube!

---

### Post by Bubs on 2007-03-09
cool i'll give that a try

---

### Post by Bubs on 2007-03-10
ok I disabled my WEP got online with the ubuntu system downloaded the network-manager-gnome installed it and restarted.  now I can't even connect to the wireless netework even without securtiy.  and I know it still works because my laptop is still online.  and I added the security again (wep) and the laptop still connects but the wireless on my desktop still does not.  

oh and I can see the network I want (six21) but I can't connect to it.

HOW do I cannect to the internet with ubuntu?  this is driveing me crazy...  my laptop is using linux (PClinuxOS) and I had little to no problems connecting to the internet even with an intel pro/2200.  but my desktop with a ralink tr2500 can't connect.

I'm not dissing Ubuntu here.  I love it for the desktop I have!  I just wanted to try something new for my laptop. 

I'm a total noob when it comes to setting up wireless!  If it doesn't work right away I have no clue how to fix it.

if you need more information I'll be happy to give it.  I just don't know what needs to be done.

and this worked before network-manager-gnome and before I added the WEP.  so I know that the wirelss card works.

any Ideas?

---

### Post by shanepardue on 2007-03-11
So network-manager sees the network, but doesn't connect with or without security? 

Which card are you using?

---

