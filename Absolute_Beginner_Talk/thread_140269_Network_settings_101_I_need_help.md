---
title: "Network settings 101: I need help"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by mattothegeek on 2006-03-05
I have finally extended my wireless network up to a room that contains my ubuntu machine via apple airports.  Now i dont know how to go about accessing the internet from that machine.

I know it is accessing the router because i can ping it.  I now need help on what settings do i need to set now so that i can access the internet.

If someone could please give this newbie a step by step script on what settings to make i would be most appreciative.  I know enough about networks to be scary but not enough to know what to do next.

Thanks in advance for your help.

---

### Post by mattothegeek on 2006-03-05
just wanted to add...i can print on the printer connected by imac so i know the ubuntu is on the network...

i simply want to be able to open a website via firefox...

Thanks for your help

---

### Post by IYY on 2006-03-05
Have you tried **System > Administration > Network**, and select your driver (ath0?) as the default gateway?

---

### Post by mattothegeek on 2006-03-05
i see eth0 and that is selected...is that what you mean?  i have a cable running from airport express to the nic

---

### Post by MetalMusicAddict on 2006-03-05
Also make sure, on your Ubuntu PC, in **System > Administration > Network > DNS Tab** you input your DNS server. Should be your routers IP. That messed me up once.

---

### Post by mattothegeek on 2006-03-08
sorry for the delay...i have been out of town.

so as i understand it, i should configure eth0 with static IP (ie. not DHCP) with an IP address (not sure what that value should be), subnet mask (populates by itself), and the IP address of my router as the gateway.  I am certain of the IP address of the router (192.168.0.3) as i am able to ping it.  Also I should put that same IP address in for DNS?  the DNS is currently populated automatically with two addresses ( i dont have them in front of me).  So should i leave those and add the router IP address or delete them and have only the router IP as one DNS?

Thanks for all of your help and i apologize for being a newbie Pain in the @ss!

---

### Post by noswal on 2006-03-08
See if the post I just made helps, same forum.

---

### Post by mattothegeek on 2006-03-09
GOT IT TO WORK!  thanks for all of your help.

One small problem now however, when connected via Ubuntu machine, my XP laptop cannot connect to the home WiFi network.  Obviously more of a network admin issue but could someone please tell me what setting changes i need to make on my Imac to allow for more than one wireless machine to access my home network?  Thanks again.

---

