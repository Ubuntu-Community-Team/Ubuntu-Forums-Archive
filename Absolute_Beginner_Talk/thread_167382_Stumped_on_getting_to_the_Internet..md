---
title: "Stumped on getting to the Internet."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-04-28
Let me start by saying that Until I started using linux I thought of myself as being pretty smart in the field of computers, and Ubuntu is changing that viewpoint. 

I have just installed Ubuntu on an old dell P2 with on-the-board lan. Network tools shows eth0 as set up and active, and I have it pointing to my router correctly. But I can't get on the internet.](*,) 

What's stumping me is that I can't find out why, and I can't find out why because that's about the only thing I can't do with my network connection. It sees the other computers on my network and interacts with them just fine. And I can ping my router, although when I try to ping another computer I get no reply. What am I missing?

---

### Post by Rikostan on 2006-04-28
Are you using DHCP or a static IP address?

---

### Post by Aximilli on 2006-04-28
[QUOTE=Rikostan]Are you using DHCP or a static IP address?[/QUOTE]

I'm sorry I forgot to mention my network stats: I'm using a linksys with static IP, and I gave this box an IP well within my range.

---

### Post by yota on 2006-04-28
What about your gateway and dns settings?

Please write down your full net config, and the output of "sudo route", so we can guess what's going on!

---

### Post by Aximilli on 2006-04-28
My DNS settings are blank, or whatever the default is for my linksys router. I'm at work right now (computer services at a college, how's that for irony) so I can't go looking at my settings atm. Sorry guys... I should have waited untill I was in front of the machine.

---

### Post by steve.horsley on 2006-04-28
Can you ping your router by IP address?
Can you ping 82.211.81.166?
Can you ping [www.ubuntu.com?](www.ubuntu.com?)

Please post the output of the command **netstat -r**

The difference between pinging that IP address and its name above is the use of DNS for name resolution.

---

### Post by michelle15g on 2006-04-28
I have a similar problem.  That's why I installed Ubuntu.  I have a LAN as well.  I have DHCP but my outgoing IP is static.  This computer's IP doesn't change as well unless I keep it disconnected for more than 3 days.
Will Ubuntu work or is there another problem?

---

### Post by Aximilli on 2006-04-28
[QUOTE=steve.horsley]Can you ping your router by IP address?
Can you ping 82.211.81.166?
Can you ping [www.ubuntu.com?](www.ubuntu.com?)

Please post the output of the command **netstat -r**

The difference between pinging that IP address and its name above is the use of DNS for name resolution.[/QUOTE]


I can ping my router by IP adress, but I can't ping another computer on my network, although I can view and access it's files in file manager. I haven't tried pinging any outside addresses, although I did try something called finger(?) in the network properties panel, and it wasn't able to find [www.google.com](www.google.com) . As to netstat, I'm going to have to get back to you on that once I get home and in front of the thing.

---

### Post by Kronoz on 2006-04-28
It sounds like a DNS issue, I had the same when I first started with FC4.

---

### Post by Aximilli on 2006-04-28
[QUOTE=Kronoz]It sounds like a DNS issue, I had the same when I first started with FC4.[/QUOTE]

It's funny you should say that, because I first installed FC5, and ran into a similar issue, but didn't find a whole lot of support and gave up on it. Ok, I'm gonna run those commands that were suggested ( I'm sharing an ethernet cable between my ubuntu machine and this one at the moment) and come back to post the output. Thanks so everyone for there suggestions:-D

---

### Post by Aximilli on 2006-04-28
[QUOTE=steve.horsley]Can you ping your router by IP address?
Can you ping 82.211.81.166?
Can you ping [www.ubuntu.com?](www.ubuntu.com?)

Please post the output of the command **netstat -r**

The difference between pinging that IP address and its name above is the use of DNS for name resolution.[/QUOTE]


So it's looking to be a DNS issue. I can ping 82.211.81.166, but when i try to ping ubuntu.com i get an error message. when I ran netstat -r I got the following output:

kernel IP routing table
Destination     Gateway    Genmask            Flags  MSS Window irtt  Iface
localnet         *               255.255.255.0    U       0     0          0    eth0
default           linksys        0.0.0.0             UG     0     0          0    eth0

 So... What does all that mean? I assume that genmask is the same as subnet mask in windows terms, so should that be 255.255.255.0 under default as well? and what are the flags? what does irtt mean?

I'm sorry that looks so bad, the post window must swallow every blank space after the first.

---

### Post by Aximilli on 2006-04-28
Well, I feel like a moron. I had never put the DNS server numbers in. Sorry for wasting your time guys. 

All the same, I'm sure I'll be needing help again, and I'm glad to see what a helpfull community you guys have here.
Thanks again!

---

