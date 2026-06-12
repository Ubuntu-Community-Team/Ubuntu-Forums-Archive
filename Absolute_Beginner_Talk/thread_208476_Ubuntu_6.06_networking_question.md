---
title: "Ubuntu 6.06 networking question"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-07-03
Hey everyone,

Shipit just delivered Ubuntu 6.06 cds to me and this time they even included ubuntu stickers which are now stuck all over the office :D 

This version is great so far. I got my modem working a lot faster this time and have had no troubles mounting and unmounting floppies which were my two big headaches with 5.10.

I have a networking question. I know zilch about networking so please bear with me. We have a windows network at work. One computer connects to the internet with dialup and others access the internet through that one computer. 

I was able to access the rest of the network and read files from shared folders with no problem. however, I was unable to browse the web even though the internet computer was connected. Any idea what I'm supposed to configure and how? Please let me know.

Sorry I'm being so long about a question I could've written up in three lines :) Thanks for your patience,

Cheers,
David the K

---

### Post by Ctrl+Alt+Del on 2006-07-03
does ping 64.233.167.99 work but [www.google.com](www.google.com) not? if yes it's a name resolution issue. Add some DNS Servers to your /etc/resolv.conf and you should be done. You can get it by running ipconfig /all on your internet computer and look for a line that says DNS-Server. Write down the following Ip Adress and add  it to your resolv.conf.
If that is not the issue you will have to provide some more detailed info.
Have you provided an IP-Adress when configuring your Network or did it work out by itself? If it worked out by itself. Post the output of ifconfig and route.

---

### Post by dckirba on 2006-07-04
Thankyou. I am on my way back to work now so I'll check as soon as I get there and let you know. does running ipconfig /all work on a windows machine because the internet machine is a windows machine. I am very bad at networking:( Will get other details and let you know. thanks again,

cheers,
David K

---

### Post by dckirba on 2006-07-05
Hey, I'm back. I tried ping from the terminal and it didn't work. I am very illiterate at networking so please wlk me through this step by step :)

I tried route and this is the output I got

ubuntu@ubuntu:~/Desktop$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

The network works great and I have no problems accessing shared folders and printers in the windows workgroup. 

Help greatly appreciated. If I can get the internet working then all is well and I might even manage to convert our office to Ubuntu :) Pretty thrilled about it.

Cheers,
David K

---

### Post by steve.horsley on 2006-07-05
There are 2 ways you might be going through the other machine to get to the internet. 

1: Using the other machine as a default gateway, a router

2: Using the other machine as a web proxy server

We really need to know which. You might be able to ask someone, but you can find out by using this command on one of the other windows workstations to see how they are doing it:
**netstat -r** 
gives us the PCs routing table. It looks much the same as the output of route on Linux. Please post the results here and we'll take it from there. If there is a default route, we'll put an identical one in Ubuntu. If not, we need details about the IP address and port numer of the HTTP proxy.

---

### Post by dckirba on 2006-07-07
Hi again! Thankyou for your answer. I hope we can work this through. Output from another windows computer in the network that can access the internet for netstat -r

Route Table
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x10003 ...00 10 4b 8a 77 91 ...... 3Com EtherLink XL 10/100 PCI TX NIC (3C905B-
TX)
===========================================================================
===========================================================================
Active Routes:
Network Destination              Netmask                Gateway              Interface 	 Metric
        	        0.0.0.0                 0.0.0.0            192.168.0.1      192.168.0.13      	         1
        	    127.0.0.0             255.0.0.0  	     127.0.0.1             127.0.0.1      	         1
      	192.168.0.0     255.255.255.0          192.168.0.13       192.168.0.13  	         1
            192.168.0.13  255.255.255.255               127.0.0.1             127.0.0.1      	         1
          192.168.0.255  255.255.255.255         192.168.0.13       192.168.0.13                   1
       	   224.0.0.0              240.0.0.0          192.168.0.13       192.168.0.13      	         1
      255.255.255.255   255.255.255.255         192.168.0.13       192.168.0.13                  1
Default Gateway:       192.168.0.1
===========================================================================
Persistent Routes:
  None

sorry the layout's so messed up. I really have to run right now but if you'd like me to post the output again in a more readable layout I will do that as soon as I get back.

p.s: i just realiseed that maybe I should've posted this in the networking forum. But I'm still an absolute beginner. So how does that work :)

Thanks again,
cheers

David K

---

### Post by dckirba on 2006-07-07
For some reason all formatting disappears when you post so here's an image: it's attached i think.

Cheers,
David K

---

