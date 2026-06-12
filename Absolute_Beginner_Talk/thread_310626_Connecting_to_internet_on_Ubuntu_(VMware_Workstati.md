---
title: "Connecting to internet on Ubuntu (VMware Workstation)"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by lkdflndflsdfs98q3 on 2006-12-01
Hi Everyone,

This is my first post and I am very new to Ubuntu and linux. I installed Ubuntu on VMware (host windows Xp home edition) but I can't get the internet to work on Ubuntu. In the VMware settings the network connection is through NAT. 

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by scc4fun on 2006-12-05
Are you able to connect in Ubuntu, but not in VMWare? or cannot connect in Ubuntu either?

<edit>
Are you connecting through a wired or wireless connection? If wireless, are you using any type of encryption (eg: WEP, WPA, WPA2, WPA-PSK, RADIUS, etc.)?
</edit>

---

### Post by compmodder26 on 2006-12-05
Any particular reason you want to go with NAT?  A bridged connection is genarally a lot easier to get going.  It will give the guest OS (Ubuntu) the same IP as the host OS (Windows).

---

### Post by Bachstelze on 2006-12-05
> **compmodder26 said:**
> Any particular reason you want to go with NAT?  A bridged connection is genarally a lot easier to get going.  It will give the guest OS (Ubuntu) the same IP as the host OS (Windows).

Nope. That's what NAT does ;) Bridged will connect the VM to the router (via the host of course but it won't share it's IP).

---

