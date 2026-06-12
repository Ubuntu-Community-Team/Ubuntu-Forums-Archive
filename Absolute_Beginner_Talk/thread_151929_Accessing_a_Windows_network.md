---
title: "Accessing a Windows network"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by transfers on 2006-03-28
I've just installed Ubuntu on a spare PC at work. It all went perfectly, except for the network configuration, which was skipped because the ethernet cable wasn't plugged in at the time. How can I see the network to get internet access etc? For obvious reasons I don't really want to go to the IT person and ask questions about IP addresses or stuff.

---

### Post by Kapre on 2006-03-28
transfers - I think you should ask your IT guy for access. Reason being is that some IT admins block access (internet or LAN) on some machines to make it secure.

K

---

### Post by transfers on 2006-03-28
But is there a way to get back to the auto configuration that was skipped in the initial setup? I also should have mentioned that it was a clean install - no dual boot.

DW

---

### Post by WoodyMahan on 2006-03-28
If you go to System - Administration - Networking you will see the Ethernet Option.  Click on Properties and you will see a setup similar to the TCP/IP properties in Windows.  Make sure the connection is enabled and setup with either DHCP or proper IP address, Subnet, and Gateway for your network.

If your Network is DHCP, then you can disable and then re-enable the connection and it should re-try to connect to and pull a new IP address.

---

### Post by transfers on 2006-03-29
That was easy! Thanks. So I don't have to keep asking dumb questions, where is the best place to look for beginners stuff like how do I see shared folders on other Windows PC's. I found Windows Network on the File Browser, but it's empty.

DW

---

### Post by WoodyMahan on 2006-03-29
I haven't gotten there yet.  Was gonna try that this week, but you know how it is.  "I can't access email... My printer won't work... My computer just blips to a black screen when I turn it on... Do you think this is a virus?...."  Maybe there will be some free time tomorrow.

---

