---
title: "Install completed, but have a question"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Retnuh on 2006-09-03
I have totally installed Ubuntu on my laptop.
I can connect to the internet through my Ethernet, but I do not see a wireless connection under my Network settings.

Can someone help me out please?

I do not even know how to add the connection under "Connections" Network Settins. There is no "Add" button.
My Netgear PCI wireless card is not working because the light isnt on.

Please help, thank you.
PS. Everyone has been great in here helping me and others I see. I guess the answer to a peaceful world, might lie in the Linux world.

---

### Post by meng on 2006-09-03
Have you got a model number for that card? Perhaps if you show the output of 
lspci
or (more restricted)
lspci | grep Netgear
we can know for sure. That would give us a starting point.
P.S. Keep in mind that informative thread titles are more likely to attract someone who can help with your problem.

---

### Post by Retnuh on 2006-09-03
> **meng said:**
> Have you got a model number for that card? Perhaps if you show the output of 
lspci
or (more restricted)
lspci | grep Netgear
we can know for sure. That would give us a starting point.
P.S. Keep in mind that informative thread titles are more likely to attract someone who can help with your problem.

Netgear WG511 v2 
54 Mbps Wireless PC Card

I just ran sudo lshw and it gets hung up on IDE with a blinking cursor, and it wont finish running.

I was able to do this earlier, but why it is doing this now, I do not know.

---

