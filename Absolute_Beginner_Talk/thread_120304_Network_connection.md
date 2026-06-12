---
title: "Network connection"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by stephan.gerlach on 2006-01-21
Hi there.

I am a absolute linux beginner. I have the following problem. I have my windows (Windows XP pro ) machine with a usb modem connected to the internet. Now I want to connect the linux mashine to the internet. 

I have installed a proxy server programme on the windows mashine ( JanaServer ) and have connected the 2 pcs with a patch cable. But I can't get it to work.

can anyone give me some help?? maybe someone has done the same what I try to do? please let me know.


Thanks

---

### Post by Joeb on 2006-01-21
Are you hooking computer to computer without using a hub or switch in between?  If so, I think you need a cross-over cable and not a standard patch cable.

Assuming you have the right cable, can the two machines see each other?  For instance can you ping the IP address of each machine from the other?

If the pinging doesn't work, you most likely have to set up manual or static IP addresses for both machines (the dhcp server in a router would do that automatically).  You might want to set one as 192.168.2.1 and the other as 192.168.2.2 and set the mask for both of them to 255.255.255.0.


I don't know if that is your problem or not, but it will give you some things to try.

Joeb

---

