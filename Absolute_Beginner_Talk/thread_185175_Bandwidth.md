---
title: "Bandwidth"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-05-31
Hello :)
I have a really short question, here it is:
How could I see how much bandwidth a specific port uses?
Example: I want to see how much bandwidth has been used on port 6667 (IRC) since reboot :)

Thanks, 
Klaidas

---

### Post by xtacocorex on 2006-05-31
I'm thinking you could manipulate netstat with cli arguments to get the stuff you need, but I'm not fully sure.

---

### Post by steve.horsley on 2006-05-31
The only way I can think of is to set up some iptables rules to specifically permit that port, and then look at the iptables counters. Or perhaps run ntop or ethereal, but both of those may be somthing of an overkill.

---

