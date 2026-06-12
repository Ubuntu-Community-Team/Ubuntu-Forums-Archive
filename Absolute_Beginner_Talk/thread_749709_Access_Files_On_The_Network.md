---
title: "Access Files On The Network"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Peck3277 on 2008-04-08
HI, I hope a question like this hasn't been asked before. I had a look around and to be honest I wasnt quite sure if it had been asked. I just got too confused.

Basically im in college on a LAN. When using windows I was using a program call softperfect network scanner. This allowed me to see and access all the shared files on the other students laptops.(also in vista i could just type \\an_ip_address_here and i cold see their shared files) But since switching to ubuntu I am unable to find a similar program or solution. Ive read about Samba but im not sure if thats what I need. 

Can anyone help? Thanks.

---

### Post by pseudo-random on 2008-04-08
Yo can view windows shares from Places > Network
You can access a machines shares with the location smb:\\computername like windows.
OR
from the command line with a tool called smbclient.
SAMBA is only if you want to act as a windows file server and offer shares.

---

### Post by Peck3277 on 2008-04-08
Sorry I was just wondering how to use this command?  smb:\\computername

I presume its used in the terminal? Does it work with ip address's?

Thanks for the quick reply

---

### Post by ibutho on 2008-04-08
It should work with an IP address as well as a hostname.

---

