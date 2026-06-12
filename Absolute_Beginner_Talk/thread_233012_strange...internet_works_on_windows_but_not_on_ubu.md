---
title: "strange...internet works on windows but not on ubuntu..."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-08-09
i'm dual-booting windows xp home and dapper, so this morning i botted dapper but got no internet so i booted into windows and everythiing was fine.  what could it be?

internet was working fine recently under dapper, and the network settings are all correct.  the weird thing is, i can't even connect to my router through firefox on dapper, so something's really wrong...

---

### Post by %hMa@?b&lt;C on 2006-08-09
who is your ISP and what service do they provide
(ie Verizon DSL (pppoe) or Comcast Cable)

---

### Post by user1397 on 2006-08-09
> **jeffc313 said:**
> who is your ISP and what service do they provide
(ie Verizon DSL (pppoe) or Comcast Cable)it's cox cable, they provide broadband cable, and it works perfectly on my windows partition, but not in my ubuntu one.

---

### Post by davebgimp on 2006-08-09
Did you install any sort of firewall manager to Dapper recently?

---

### Post by %hMa@?b&lt;C on 2006-08-09
> **erik1397 said:**
> it's cox cable, they provide broadband cable, and it works perfectly on my windows partition, but not in my ubuntu one.
hmmm... Have you ever had this working under Linux?
try this
[http://ubuntuforums.org/showthread.php?t=144714&highlight=cox+cable](http://ubuntuforums.org/showthread.php?t=144714&highlight=cox+cable)
if that doesnt work, try posting the results of ifconfig and lspci here and hopefully we can get this fixed

---

### Post by AndyCooll on 2006-08-09
davebgimp is heading in the right direction. It is a Linux related setting that's causing the problem, nothing to do with your ISP.

Can you ping your router?

---

### Post by user1397 on 2006-08-09
> **davebgimp said:**
> Did you install any sort of firewall manager to Dapper recently?no

---

### Post by user1397 on 2006-08-09
> **jeffc313 said:**
> hmmm... Have you ever had this working under Linux?yes, flawlessly.  as i have already mentioned, it was working fine yesterday, its just that this morning it stopped working.

---

### Post by user1397 on 2006-08-09
> **AndyCooll said:**
> davebgimp is heading in the right direction. It is a Linux related setting that's causing the problem, nothing to do with your ISP.

Can you ping your router?nope i cannot ping my router, and ifconfig shows some weird ip address, not in the regular format.

---

### Post by steve.horsley on 2006-08-09
Like what?

---

### Post by user1397 on 2006-08-09
> **steve.horsley said:**
> Like what?see it's hard to get the exact thing because i am only on one computer so i have to boot into windows, boot into ubuntu, boot back into windows and so forth.  but i guess i have no other choice, so i'll do that, but not now, because im busy.

---

### Post by user1397 on 2006-08-11
fixed it!  i realized that i had changed a router setting not too long ago, so I just changed it back to the default setting and it worked!  the setting was how many ip addresses is the DHCP server supposed to give out to my computers.  i put it back to the default 10 from 5.  problem solved :D

---

