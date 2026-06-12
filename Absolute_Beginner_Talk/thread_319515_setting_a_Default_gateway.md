---
title: "setting a Default gateway"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
I want to set up the gateway address for my ubuntu machine . The machine is in a large network and i have to point to a router that knows how to bridge to a number of subnets 

Thanks in advance

---

### Post by dbott67 on 2006-12-15
This is the command you would use from the terminal.  Of course, you would need to change the gateway address (192.168.1.1) and device (eth0) to suit your particular configuration:
```
route add -net default gw [COLOR="Red"]192.168.1.1[/COLOR] dev [COLOR="Red"]eth0[/COLOR]
```

-Dave

Note: you might need a 'sudo' in front:
```
**sudo** route add -net default gw [COLOR="Red"]192.168.1.1[/COLOR] dev [COLOR="Red"]eth0[/COLOR]
```

---

