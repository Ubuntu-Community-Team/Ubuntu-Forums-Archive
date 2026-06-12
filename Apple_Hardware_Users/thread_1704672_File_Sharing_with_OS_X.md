---
title: "File Sharing with OS X"
date: 2011-03-11
forum: Apple Hardware Users
---

### Post by Nwwmac on 2011-03-11
I'm having trouble with file sharing between my iMac and Linux PC. The  Linux machine is running Mint 10 64-bit and the Mac is running Snow  Leopard 10.6.6. 

The Linux machine can access the Mac's public folder with no problems. 

The iMac can see the Linux machine - it shows up in the Finder as a PC.  It can't access it at all. The "connect as" button gives an error saying  the Linux server may not exist or may not be available, please  re-check. Using the "Go" menu and typing in the IP (afp://XX.X.X.X)  gives no result - it just tries and tries and ends with the same error. 

I know very little about networking but I think the two are using samba.  The iMac has Samba turned on, and using SWAT on the Linux machine shows  that it is running version 3.5.4. SMBD and NMBD are running and  Winbindd is not. SWAT also shows no active connections. 

My question is, what do I have to do on the Linux box so that when the  iMac tries to connect, I get prompted for my username and password, so  that the public folder there can be accessed? 

I have tried turning off the firewall on the Linux machine but that made  no difference. I did edit the public folder's properties so that  sharing is enabled, but only by me, ie. under group I chose my username.  

Both machines are connected to a Time Capsule via Ethernet. 

Suggestions for how to proceed would be very welcome! :smile:

---

