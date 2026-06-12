---
title: "Live CD Provides No Internet Access"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by RonnieV on 2007-08-01
I'm evaluating Ubuntu on a Dell Dimension P3 with 256 MB of memory.  I am unable to access the internet when connected to my wired Belkin router or even when I bypass the router and connect directly to my cable modem.  Can I reasonably assume the problem may be that Ubuntu has a problem with my NIC?

TIA for your thoughts.

---

### Post by ddrichardson on 2007-08-01
Not neccesarily - check to see if the device is recognised in Device Manager. Then check if a driver's loaded (sudo lshw -C network from a terminal should do it).

Then you know for sure if the card isn't recognised.

---

### Post by RonnieV on 2007-08-01
Thx for the post.  Ubuntu tells me it recognizes my card.  If it recognizes the card and loads the correct driver, where do I go from here?  Is is generally necessary to configure settings to access the internet, even when bypassing a network?

---

### Post by ddrichardson on 2007-08-02
I'll post more later. little busy ;-)

---

### Post by ddrichardson on 2007-08-02
We need to check where the problem lies. The most obvious thing that springs to mind is IPv6 not being supported so open a terminal and type:
```
gksudo gedit /etc/modprobe.d/aliases
```
Find the line that says:
```
alias net-pf-10 ipv6
```
Change it to read:
```
alias net-pf-10 off
```

Reboot and try using the Network Manager to get your connection up. If you're still having trouble you can try opening a terminal and typing:
```
ping -c 3 82.211.81.158
ping -c 3 www.ubuntu.com
```

If the first line returns packets and the second doesn't then there is a DNS problem.

---

### Post by Raineer on 2007-08-02
Remember he's on the Live CD so there's only so much he can do.  The last part (pings) can still apply.

---

### Post by ddrichardson on 2007-08-02
> **Raineer said:**
> Remember he's on the Live CD.

Whoops forgot about that.

You can still confirm if its a DNS problem or an IP address problem though. ifconfig should give some useful output.

---

### Post by RonnieV on 2007-08-02
As I initially suspected, the problem was Ubuntu's problem with my NIC card.  I replaced it with another one from an older PC and it worked fine.  Thx for taking time to offer your suggestions.

---

