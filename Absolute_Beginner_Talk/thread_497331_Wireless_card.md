---
title: "Wireless card"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Mrhankymk on 2007-07-10
Hey,

I just installed Ubuntu successfully and am amazed by its speed compared to my current XP. So in turn I want to start using it every day (programming, watching videos, etc.). The only problem is I can't without the Internet.
I looked into my network connections (that's what it's called in Windows.. Forgot what it is in Ubuntu but you know what I mean hopefully) and I saw something about 2wire which I remember seeing before in Windows although I don't see it when I switch over to Windows (dual boot). Although on the Linux machine I can't see the network I need to connect to. I don't want to advertise the SSID so we'll be calling it Fred :-P. The network is verified via mac address so in the Windows driver of my networking card (a Blitzz Super G wireless PCI card) you see a network with a blank SSID but in Linux I see nothing of it so I am assuming I can't see it in Linux because I need to be authenticated. Although my mac address should stay the same on both OS's. If I lost you I'm sorry. I've pretty much lost where I am in the story myself. But bottom line does this mean my card isn't recognized my Linux and I need to use a program to use my current Windows driver? Or does this just mean I need to change my hostname or something so the router can recognize me?

---

### Post by dmfield on 2007-07-10
bit confused, sorry, q quick test to see if your wireless card is working, is to go to the termin and type 

sudo iwlist scan 

If it comes back with any networks then your card should be working..

Try turning off the MAC stuff on the router, just to gain a connection, once you have done that, then revert back to the previous settings. The names you have given the ubuntu box work on Layer 3 IP traffic, but MAC addresses are Layer 2, so that shouldn't have any bearing..

I might be wrong, but thats how i understand it..

---

### Post by Inxsible on 2007-07-10
I use MAC address filtering along with WAP. So that shouldnt be a problem. 
 
After you see that your card is working by following the earlier poster's instructions,try this.
 
In the top right corner, single click on the network icon and then select 'Manually Configure Network' or something to that effect. I dont rbr the exact terminology there since I am not on my Ubuntu machine now.
 
Then put in the SSID that you have setup with your router. Enter the password if any, and see if that works.

---

