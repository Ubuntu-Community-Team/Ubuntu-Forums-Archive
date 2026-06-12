---
title: "Help with configuring netowk to get internet connection"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-26
I keep on losing my Internet connection and now I can not get any connection at all when using my router with my cable modem.
Please view the image attached to this post. It shows a comparison of details on the status page of the router with output of <ifconfig> I have highlighted what I think might be the problem but I am sure I am way off base. Why is ubuntu not reading my router?(Which it perfectly used to for the past 6+months). Also, Instead of rebooting everytime I change something in the network configuration, is there a way to just get that part rebooted so It can be read by the OS again? tried 
```
/etc/init.d/networking restart
``` that gave me a number of errors. I am very anxious to get this back online so I can go back to using Ubuntu and also port forward my webserver to a port not blocked by my ISP, so I can listen to my music from work...will take any suggestions....
Thanks in advance.. this community has been extremely helpful in the countless issues I've had in the past
[IMG]http://www.flickr.com/photos/habtish/333685075/[/IMG]

---

### Post by jonathan.lees on 2006-12-26
habtish, is your gateway configured correctly as 192.168.1.1?

---

### Post by habtish on 2006-12-26
> **jonathan.lees said:**
> habtish, is your gateway configured correctly as 192.168.1.1?
IN the Network setup screen, the only time I can edit my gateway is if I am using a static IP configuration, which I have tried and failed. I  don't get the option to specify the gateway when I select Automatic Configuration(DCHP ). How do I do that(specify my gateway and broadcast and those things that my router is showing as one and are listed different under my ifconfig)?
 Please view attachment for a clarification in what I was saying about the gateway and DHCP, thanks!~

---

### Post by jonathan.lees on 2006-12-26
ok, first just try to ping your router. Open a terminal and type ping 192.168.1.1. If you get a response then your ethernet card, cable and router (Lan config) are ok. If there is no response you'll need to test each individual part > ethernet card > cable > router.

Secondly you could try a traceroute. In the terminal type traceroute google.com and look to see where it is failing. If you get a command not found when you run traceroute, you will need to install it:


sudo apt-get install traceroute

---

### Post by blackmh on 2006-12-26
Try to ping [www.google.com](www.google.com). If says destination unreachable, try to ping 209.85.135.104 (google) to see if name resolving works correctly. If you manage to ping IP address, add nameservers to ubuntu network properties - either IP of your cable modem (better solution) or nameserver IP of your ISP. I had same problem, DHCP server would assign IP address and gateway but failed to supply DNS information.

---

### Post by habtish on 2006-12-26
> **blackmh said:**
> Try to ping [www.google.com]("http://www.google.com"). If says destination unreachable, try to ping 209.85.135.104 (google) to see if name resolving works correctly. If you manage to ping IP address, add nameservers to ubuntu network properties - either IP of your cable modem (better solution) or nameserver IP of your ISP. I had same problem, DHCP server would assign IP address and gateway but failed to supply DNS information.
My router was picking up the current DNS info from my ISP, which I had updated in my Network config in Ubuntu. Also, while connected to through the router, I can logon to the admin page by hitting 192.168.1.1 on the web browser, so I know my ubuntu is connecting to the router, I just don't seem to be able to get a connection from the router to the outside world or vise-versa, I will change my wiring, reboot and try all the suggestions above, will post results...

---

### Post by habtish on 2006-12-26
OH well, things seem  to be working now.. Here's what I did and what I had tried a number of times yesterday and failed... shut the computer down, disconnected my ethernet cable from the cable modem, cut the power off of the cable modem and the router, disconnected the coaxial cable going into the modem,+disconnected the ethernet cable that ran from the router to the modem (which I hadn't tried the other times and didn't think would make a difference).. I left things like that for about 5 minuttes, connected cables modem>router>PC, started ubuntu and voila I have an internet connection... not really sure what the problem was and what fixed it.. guess there are some things a noob is never meant to know... my next step is setting up an internal static IP so my port forwarding works consistently independent of DCHP renews...thanks for all the help.. I guess I will come back and whine more if setting up  a static ip breaks my connection, can consider this thread resolved for now though :)

---

