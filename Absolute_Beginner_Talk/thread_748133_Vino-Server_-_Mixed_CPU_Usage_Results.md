---
title: "Vino-Server - Mixed CPU Usage Results?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by KevinD_Atl on 2008-04-07
[FONT="Verdana"]I find that if I'm in my local network and use VNC viewer through an XP Pro machine to Ubuntu 7.04, the CPU goes and stays on the 40% range and the sent network packets are high also, about 190 KBs.

When I'm remote and forward the port into my WAN (external from my network), then the CPU is great, like 5%

Anyone know why I would have WORSE results in the local LAN, with 100 MBs?  Seems like it would be totally the opposite of what I'm experiencing....wierd...[/FONT]

---

### Post by jkeyes0 on 2008-04-07
> **KevinD_Atl said:**
> [FONT="Verdana"]I find that if I'm in my local network and use VNC viewer through an XP Pro machine to Ubuntu 7.04, the CPU goes and stays on the 40% range and the sent network packets are high also, about 190 KBs.

When I'm remote and forward the port into my WAN (external from my network), then the CPU is great, like 5%

Anyone know why I would have WORSE results in the local LAN, with 100 MBs?  Seems like it would be totally the opposite of what I'm experiencing....wierd...[/FONT]

With your VNC viewer, what speed setting are you using? I know Ultravnc for windows uses an Auto-select setting by default, so the faster the connection, the more resources it's going to use. You might try lowering the speed to see if it makes a difference.

---

### Post by KevinD_Atl on 2008-04-07
That makes sense, but I have it set on LAN at the moment, and will test that out later today. 

Are there any alternatives to the vino-server that use less resources, and use the VNC protocol?

---

