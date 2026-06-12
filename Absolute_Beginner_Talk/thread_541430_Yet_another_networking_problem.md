---
title: "Yet another networking problem"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-09-02
I just installed Feisty on my family computer, and I'm having some network problems that I don't recall having when I set up my own machine. The computer in question connects to the internet and our home network through an Ethernet cable, and we can get to the net with no problems. This computer can see the Windows Network, but not any of the computers on it, and the other computers (one Feisty, one XP) can see this computer, but not access its files. I have installed Samba, and set up an account to access this computer, but still cannot access its files, nor see the other computers from it.

---

### Post by louieb on 2007-09-03
Heres the Samba guide I used. Works great.
[HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605&highlight=server")

---

### Post by Hitchhiker42 on 2007-09-03
I tried the guide (wish I had known about it when I was setting up my own computer!), but it did not appear to make any difference. Our Win computers can see this computer, and the fact that it is running a samba server, but they say access is denied when we try to get to the shares. From beaver (the linux computer in question), we can see that there is a windows network, but cannot see the workgroup, to say nothing of the other computers on the network.

---

### Post by whereareyoutakingme on 2007-09-03
i am having...seemingly so far...the exact same problem.  i have a fiesty box in my room and a windows box in my living room.  they are both connected to a router via ethernet cables...the only interesting thing about the router set up is that for some reason it won't receive a WAN ip address from my internet provider, so i've plugged the ethernet cable running from the internet port in the wall, directly into a LAN port.  this essentially uses the router as an ethernet splitter.  i have given the two computers static IPs and auto IPs, both of which have the same issue.  the windows box can see and fully access my samba share on the linux box (i've even mapped a network drive to it), but the linux box only sees the existence of the WORKGROUP workgroup of windows, however when i try to access it nothing happens, or it says that it can't open the WORKGROUP workgroup.  i had this all set up pretty much exactly the same before i moved into my new apartment and it worked fine...what have i done wrong after the move?

---

### Post by Hitchhiker42 on 2007-09-06
Well, this computer still can't access the network, and I don't have the first clue where to start troubleshooting, as I am still a noob. So, in hopes that someone can provide some insight, BUMP!

---

