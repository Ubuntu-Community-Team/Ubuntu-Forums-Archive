---
title: "Networking Newbie Needs Help Adding Workstation"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Stervyatnik on 2006-12-03
Hello, all!

I am pretty new to Ubuntu, but I have installed it on two computers, which I'm trying to network to get my "feet wet" in networking. Here're my fledgling network particulars:

Computer 1: 800Mhz, 20GB HD, 256MB RAM
OS: Ubuntu Linux Server i386 6.06
Network Name: velikan
IP Address: 192.168.0.1
Subnet Mask: 255.255.255.0

Computer 2: 800Mhz, 20GB HD, 256MB RAM
OS: Ubuntu Linux Desktop i386 6.06
Network Name: studentka
IP Address: 192.168.0.2
Subnet Mask: 255.255.255.0

I am using a D-Link 8-port switch 10/100Mbps switch (Model Number: DSS-8+)

I did a complete install of the Linux on each box, and I chose the "Install LAMP server" option on the server box (computer 1). On the server, I manually configured the DCHP settings, and left the "Gateway" option blank. (I don't plan on connecting to the Internet yet.)

I did an "ifconfig" command on each computer, and the only difference I can see is the computer 1 shows:

   UP BROADCAST RUNNING MULTICAST

Whereas the ifconfig on computer 2 shows:

   UP BROADCAST MULTICAST

The eth0 result for the ifconfig command on each computer shows the appropriate IP address and Subnet Mask.

I also modified the /etc/hosts file on each computer, adding the lines to each file:

   192.168.0.1 velikan
   192.168.0.2 studentka

The problem is, having done all that, I can't ping the other computer from either station. I can't ping 192.168.0.2/studentka from 192.168.0.1/velikan, and vice-versa. The NIC card on the back of "velikan" shows green and yellow traffic lights, and the port on the switch shows connected. BUT, on "studentka," there are no traffic lights on the NIC, and no "connected" indicator on the switch.

What am I doing wrong? I figure if I can get one station on, later, I can use my "vast experience" to add others. But so far, my "vast experience" is nil, so I'm looking for any help.

Thanks in advance!

---

### Post by apjone on 2006-12-03
Even if you do not wish to access the net off them yopu need to specify the GATEWAY Address

---

### Post by steve.horsley on 2006-12-03
A bit of googling got me that RUNNING means the port is "ready to accept data". And unplugging the cable from my Ethernet port makes the "RUNNING" disappear from my ifconfig. So I guess that RUNNING means the cable is plugged in and everything is working properly. On that basis, it seems there is something wrong at with computer 2.

---

### Post by Stervyatnik on 2006-12-03
Thanks all, for the inputs. I both added a gateway address AND I checked the NIC card, and it WAS not working. Works now, though, and am able to ping each computer on the network. 

Now, to figure out how to make drives/directories/files available, and enable MySQL across the network, and I'll be smokin'!

Thanks again, everybody!

---

