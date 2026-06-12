---
title: "Is there a practical usage for 2 NICs on a MOBO?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-01-29
I have a MOBO with 2 built-in Network ports, they have caused my Internet connection much confusion under Linux.  Since this never happened during Windows XP sessions it got me curious.
Is there any practical usage for 2 NICs on a MOBO?

All I can think of is that when one gets short-circuited then you will have one spare to use directly.  But then the MOBOs default configurations was enabling both 2 NICs so they must be able to serve a higher purpose other than to confuse Network settings under different OS's.

---

### Post by Paerez on 2007-01-29
You can use the computer as a router. So one NIC plugs into a cable modem or other internet connection, and the other plugs into a HUB for other computers to use.

---

### Post by Zzl1xndd on 2007-01-29
> **Paerez said:**
> You can use the computer as a router. So one NIC plugs into a cable modem or other internet connection, and the other plugs into a HUB for other computers to use.

This is probably the intended use although it isnt always east to set up. Other than this I couldn't think of any other use.

---

### Post by PurplePenguin on 2007-01-29
Aren't there some DSL plans that let you use two DSL modems and lines in order to double your bandwidth?  Or am I confusing make-believe and reality again? :D  (it happens)

---

### Post by Zzl1xndd on 2007-01-29
I dont see why this wouldn't work now that you mention it. Kinda like shotgunning dialup modems back in the day. Although I know of no provider in canada that offers it. I spouse you could sign up for 2 accounts but iv never tryed it nor have I heard of anyone trying it. Most times I hear of this people use a load balancing router.

---

### Post by Paerez on 2007-01-29
I know people used to use dual ISDN connections. Mainly businesses. And also it was way back in the day.

---

### Post by JamieC on 2007-01-29
Isn't it for redundancy?

---

### Post by irish_flu on 2007-01-29
Several reasons:


-Yes, you can use the machine for "connection sharing" with two NICs.

-Also, as has been said, redundancy is nice.

-You could also put 1 NIC inside the firewall (connected into your switch) for accessing shared drives, printers, etc and the  other NIC outside the firewall for running an Apache Webserver or something (not the most secure way to roll, but you could do it).

-and you might just do it to have different applications using different IPs on different NICS, that way the applications aren't fighting for bandwidth.

---

### Post by jingo811 on 2007-01-30
How complex this subject is.

---

