---
title: "Power of Command"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2007-02-20
Hey guys,

I was just wondering if they was some way i could make a script, command, or  something like that that would forward specific ports on my router in order to run Azureus. Then when I close Azureus I was hoping for the command or script to automatically close the ports I just forwarded. The reason I ask this is because all the other computers in my house get their IP addresses dynamically so I cant permanently use a static IP.  

Perhaps by implementing these commands...

iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT 

Thanks,
MC

---

### Post by annda on 2007-02-20
i believe ports are closed or opened by your router. iptables just works for your computer.

maybe if you could set a static ip high in your router's range (like the last available address), no other users would get is assigned via the router's dhcp, so no connections would be forwarded to them...

just an idea.

---

### Post by mconway0003 on 2007-02-20
Well I have a wired connection with an ethernet chord but those commands seemed to work for me before.

---

### Post by mconway0003 on 2007-02-20
> **annda said:**
> i believe ports are closed or opened by your router. iptables just works for your computer.

maybe if you could set a static ip high in your router's range (like the last available address), no other users would get is assigned via the router's dhcp, so no connections would be forwarded to them...

just an idea.

that is not a bad idea at all, thanks

---

