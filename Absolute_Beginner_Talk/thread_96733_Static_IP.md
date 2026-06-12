---
title: "Static IP"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-11-29
Am I missing something here? Trying to congigure my Netgear router.

So I go to whatismyip.com, copy my ip address, system->admin->Networking, select my ethernet connection, click propeties, select static IP address form the drop down box and paste the IP address.

The subnet mask field is automatically populated with 255.0.0.0.

I click OK and as soon as I do that I can't connect to any websites, until of course I reselect DHCP.

Any ideas?

---

### Post by Remmelas on 2005-11-29
If you are behind a router, it is likely that your machine is using private network addresses rather than the public one that your router is using.  an easy way to test would be to open a terminal and see what is being assigned by DHCP as your ip address.  The command to do so is 'ifconfig', and it will print your network info to the screen.  
From what you have said, it almost sounds as if you are assigning your routers public IP address to your internal PC, which usually won't work.

---

### Post by marks_linux on 2005-11-29
The web site will be showing the ip of your router connection to your ISP etc.

On linux box type ifconfig.

your actual machine IP within the network served by your router (i.e. all the machines using your router to get out to the web) will be listed against inet addr:

Thats assuming I'm understanding your question?

---

### Post by Matt Houston on 2005-11-29
Thanks for the replies. Yes you are understanding my question, I tried this again with the IP I got using ipconfig and inet addr IP under eth1, no dice, same thing. Any idea what I could be doing wrong?

---

### Post by Herman on 2005-11-29
I can't see what you are doing wrong, but here's the way I set my static IP for inside my LAN and it works for me:
1. System-->Administration-->Networking (enter password)
    -->Network Settings-->Ethernet Connection-->'Properties' button.
2. (a) 'ticked' box for 'enable this connection'
    (b) configuration feild: set to 'Static IP address'
    (c) IP address feild: type in any number between 192.168.1.100 and 192.168.1.255
         (On my LAN, there are four PCs dual booting, and the bottom four numbers
         sometimes get taken by Windows machines using DHCP, so I keep clear of the bottom four numbers. ( I leave .100 to .104  for Windows Network).
    (d) the subnet mask feild automatically sets itself to 255.255.255.0
    (e) gateway address; 192.168.1.1
         I got this gateway address from my router manual, it might be the same for others or maybe not, I'm not too sure. Try it and if it doesn't work you might need to look yours up in your router manual.
That works for all computers in my LAN, for my brand of router, and whatever number I set in the address field will be the number I get after typing   ifconfig     in a terminal.
This is for setting your internal IP address inside your LAN.
The outside (ISP) IP address is the one can find out from 'what is my IP', and that's probably not relevant to your present problem.

Will setting a static IP address really help you configure your router? Did you mean 'configure your router', or 'configure your network'? The reason I set my IP address to static is so I can use SSH networking between Ununtu boxes in my LAN. Before that my router always worked fine without any doing any special configuring at all. Well it won't do any harm I suppose. Hope that helps, good luck with it!:smile: 
(Herman)

---

### Post by Matt Houston on 2005-11-29
Herman you are a giant among men. Took a bit of fiddling around but I got it working, thanks.

---

