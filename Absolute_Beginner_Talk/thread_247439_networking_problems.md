---
title: "networking problems"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by tponte on 2006-08-30
Hi all,

I'm using ubuntu 6.06 and been having a few problems with the internet configurations.

I haven't been able to connect to gaim, msn or even to download updates.
I did some research and found out that it could be due to IPV6. I edited file /etc/modprobe.d/aliases to change line
alias net-pf-10 ipv6 to
alias net-pf-10 off
I believe I've turned it off, since ip a | grep inet6 doesn't return anything.

Still I cannot connect get upgrades or even telnet a like google.com. When I try it says Trying 1.0.0.0... and does nothing. If I ping the host before trying to telnet, it seems to resolve the address and then telnet works just fine.

Can anyone help me to fix this?

Thanks

---

