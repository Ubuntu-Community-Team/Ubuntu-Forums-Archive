---
title: "Problem while using VNC + RDP"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by bhargava on 2007-09-09
Hello,

I just installed Ubuntu 7.04 and successfully configured it to connect to my Windows XP machine at work using VNC and Gnome-RDP. Everything is fine with that.

However, I do have a small problem. On my Ubuntu machine, I am unable to surf (web, IM) from the time I connect to VPN. As soon as I disconnect VPN, all these things start working fine. I know there is one setting in Windows which says "Use this as the default gateway" for VPN Connections. When this is checked, problem I am experiencing will show up in Windows too (and obviously when unchecked, I am able to use BOTH vpn and internet at the same time).

Can anybody let me know if there is such a thing which enables to use both VPN and local internet at the same time in Ubuntu?

Thanks,
Bhargava

---

### Post by 22bsti on 2007-09-22
if you are still experiencing this,
what you are experiencing is not uncommon, nearly all vpn's will do this.  what you need to do is make sure that your vpn client is setup to allow you to use the default gateway on your local network and make sure to add a route to use the remote dfg for the vpn

---

