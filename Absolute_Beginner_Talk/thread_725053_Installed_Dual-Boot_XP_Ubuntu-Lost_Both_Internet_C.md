---
title: "Installed Dual-Boot XP Ubuntu-Lost Both Internet Connections"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Newvin on 2008-03-15
Hello,
   Yesterday I installed Ubuntu on a system that already had Windows XP.  Everything went smoothly, and I can now dual-boot.  The only problem is that I can get neither my XP or nor the Ubuntu Internet connection to work.  I've scoured both Windows and Ubuntu threads exstensively and haven't had any luck.  I'm new to the linux networking game, but here are a few things I can tell you:

   I have a cable modem hooked up to a router hooked up to the dual-boot machine.  I have two other computers hooked to the same router with working internet connections (so I imagine the modem and router are ok). 

/etc/network/interfaces looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

When I type "ifconig" at the terminal, I get entries for eth0, eth0:avah, and lo

Pinging the router gives a series of "Destination Host Unreachable"

Any help in this matter would be greatly appreciated.

Thanks

---

### Post by glennric on 2008-03-15
Installing Ubuntu shouldn't affect whether or not the network works in Windows.  I would say there is a good chance something is wrong with your network somewhere.  Have you checked all of the network cables and your router?  What happens if you try to open the router's configuration page in a browser in windows?

---

### Post by bumanie on 2008-03-15
I am not brilliant at  networking problems, but have you tried to reset the internet connection through windows set up wizard? That's where I'd start and ensure the connection is set dhcp. The issue with ubuntu may be different. I assume you're using 7.10. Very often, (not always) the issue with connecting 7.10 is due to an ipv6 issue that does not usually worry windows. Try the windows internet wizard and post back. 
Or else in ubuntu open firefox and type in the address bar
about:config --> enter
In the filter type ipv6 --> enter
Right click on the line that appears, then left click on toggle and change the value to true. Reboot ubuntu and see what happens.
If neither of these work you will have to wait for someone more knowledgeable than myself.

---

### Post by Newvin on 2008-03-15
Thank you both for your quick responses -- Here are the results:

1) I Toggled the ipv6 value to True and Rebooted Ubuntu 

--No Dice

2) When I try to enter router config from browser in Windows, I get "The connection has timed out".  Doing the same thing in Ubuntu, I get "Unable to Connect".  However, I can successfully enter router configuration from 2 other machines connected to the same router.

I've tried static and automatically obtained IPs in Windows without success.

At this point, I'd be happy to get either internet connection working.

Thanks again.

---

### Post by fourscore on 2008-03-15
Have you tried connecting with a different cable and  also connecting to a  different port on the router

---

### Post by bumanie on 2008-03-15
It is very odd that the other two computers can get addresses and connect to the internet, but the 'main machine' cannot. I will think some some more, but frankly, at this point have no idea what to suggest as the first two suggeations failed. I assume you have rebooted the computer so as to 'reset' everything - sometimes something that simple works, but I assume you've done that already.

---

### Post by Newvin on 2008-03-15
I tried a new (tested) cable in a different port on the router.  Same results.  The computer from which I am writing this post is on the same router as the foobarred machine.

Thanks

---

### Post by glennric on 2008-03-15
Just because one port on a router works, doesn't mean the others do.   I have a router with four ports, only two of which work at all.  In fact I have to have a network cable that goes nowhere plugged into one of the dead ports in order for the two ports that do work to work at all.  It is also possible that the network card in that computer has gone bad.

---

### Post by Newvin on 2008-03-15
Is it possible that Installing Ubuntu could have fried my ethernet card some how?  Right up until the point when I installed it, I was connected to the internet in windows.

Thanks

---

### Post by glennric on 2008-03-15
I don't think that installing Ubuntu would fry the card.  It is something that could happen at any time to any network card in any universe ...
Hardware dies.  It happens.  Sorry, if that is the case but network cards are cheap.  I had a network card go bad (and it took two ports on the router and another network card on another computer with it).  There is a good chance there was a lightning strike that evening that hit the internet cable.

---

### Post by fourscore on 2008-03-15
is the network card properly installed.  Have u checked under device manager in windows for the status of the network card.
What is the make of the card.

---

### Post by Newvin on 2008-03-15
Thanks to all for the helpful advice, I solved my problem by installing a new ethernet card.   Connected in both Ubuntu and Windows.

What a helpful community!

---

### Post by ghost_ryder35 on 2008-03-15
Congrats!

---

