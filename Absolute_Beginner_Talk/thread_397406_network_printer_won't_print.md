---
title: "network printer won't print"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by sculptorjay on 2007-03-30
Hello, I am new to Ubuntu Linux and I like everything about it so far. The only problem I have is with connecting a network printer to a computer I put Ubuntu on at work. The printer is a HP Laserjet 2100M. Could someone tell me how to install it. When I add it as a new printer, it shows up on the desktop but doesn't print. I don't know what I am doing wrong. 

Thanks for any help you may be able to provide. 

Jay

---

### Post by NikoC on 2007-03-30
Which guide did you use? Most of the time it goes like this:
Gnome main menu > system > administration > printing 
New printer > Network printer :
IPP: if it is a printer directly connected to the network and thus has its own IP > enter the IP address > forward > install correct driver

Or:

Samba: if it is printer that is shared on a windows machine (make sure the printer is shared on the XP machine, know the name of the printer and the name or IP of the host you are installing it on)
Enter the hosts' name or IP, the printer share name, your login and pass that you use on your XP machine (make sure that your username has access to the printer on XP: right click on the printer in XP printer settings and there should be a share tab available in which you can select a specific user on the XP machine or  everyone) > install the printer driver for your machine

This last method worked for me, though after some searching I found out that spaces in usernames and passwords don't do well in samba!

---

### Post by sculptorjay on 2007-03-30
Thank you for your suggestions. How do I find out my printer's IP?

---

### Post by chaplanger on 2007-03-30
> **sculptorjay said:**
> Thank you for your suggestions. How do I find out my printer's IP?

I've attached an instruction sheet which helped me.  My printer server is running Ubuntu and my other computer is running WIN 2K.

Hope this helps

---

### Post by NikoC on 2007-03-31
> **sculptorjay said:**
> Thank you for your suggestions. How do I find out my printer's IP?

So the printer is directly connected to the network, not via a host? Well I don't know for your printer, but if it has a display there should be some settings in there that allow you to set/change/obtain the ip address, otherwise you can try checking out the manual on where to obtain the ip.

---

### Post by sculptorjay on 2007-04-13
My friend googled "hp configuration page" and came up with instructions for how to get the printer to print out complete information about itself including  host name and the ip address. (Push start and go buttons simultaneously.) Using the information we were able to set up printing and it worked fine.

---

