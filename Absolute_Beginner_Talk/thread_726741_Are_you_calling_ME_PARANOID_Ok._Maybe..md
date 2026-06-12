---
title: "Are you calling ME PARANOID??? Ok. Maybe."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by [ARB1D3_[00L3R on 2008-03-17
So I have seen a few threads, and have a little annoyance that could add up to a whole lotta nothing...but just in case...

I am running cox high-speed yaddayadda, and I am recieving packets like mad. My connection is not choking, but I get paranoid since i'm recieving packets non-stop; and I mean a continuous flow.

pulled up wireshark and got a whole lotta ARP protocol being used by single source. can I block the source? am I just being paranoid?

tia,

[ARB1D3_[00L3R

---

### Post by Oldsoldier2003 on 2008-03-17
> **'[ARB1D3_[00L3R said:**
> So I have seen a few threads, and have a little annoyance that could add up to a whole lotta nothing...but just in case...

I am running cox high-speed yaddayadda, and I am recieving packets like mad. My connection is not choking, but I get paranoid since i'm recieving packets non-stop; and I mean a continuous flow.

pulled up wireshark and got a whole lotta ARP protocol being used by single source. can I block the source? am I just being paranoid?

tia,

[ARB1D3_[00L3R

depends on what host is sending the packets :) arp isn't necessarily evil.

---

### Post by mozetti on 2008-03-17
run the IP through the WHOIS database and see if there's a reason someone there should be sending you ARP packets.

---

### Post by The Cog on 2008-03-17
Are the ARP packets looking for your IP address or for other peoples IP addresses? Maybe  the cox network uses bridging rather than routing, in which case you will receive an ARP packet every time any cox user tries to connect to anything. Infected bots trying to scan / infect other PCs should be obvious because of all the ARP packets they generate.

---

### Post by [ARB1D3_[00L3R on 2008-03-17
wireshark>>

No.     Time        Source                Destination           Protocol Info
      1 0.000000    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.196.11.8?  Tell 72.196.10.1
      2 0.143063    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.213.43.22?  Tell 72.213.43.1
      3 0.143065    Riverdel_c2:b3:01     Broadcast             ARP      Who has 68.226.77.16?  Tell 68.226.77.1
      4 0.143067    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.213.43.44?  Tell 72.213.43.1
      5 0.143068    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.213.43.5?  Tell 72.213.43.1
      6 0.163050    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.213.43.26?  Tell 72.213.43.1
      7 0.163053    Riverdel_c2:b3:01     Broadcast             ARP      Who has 72.213.43.30?  Tell 72.213.43.1


can i block Riverdel_c2:b3:01 ?

---

### Post by The Cog on 2008-03-18
I wouldn't if I were you (and I don't know how). That MAC address is sourcing packets from multiple IP addresses, which means it's probably your default gateway too. You can try pinging something and see what MAC address those pings go to/from to prove the point.

---

### Post by [ARB1D3_[00L3R on 2008-03-18
In a strange way "The Cog", you just answered my question...Thanks!

---

