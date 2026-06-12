---
title: "Problem with web browsing"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by linux_crazy on 2007-03-31
I have a problem with web browsing. I have installed many Linux distros (last Kubuntu 6.10). They all have one thing in common. The only web browser which 
works for me is konqueror. I have intalled mozilla and opra  but both of them 
freeze on 'connecting to ...' then 'connection timeout' .My computer is connected to internet through Actiontec Wireless DSL Modem--->LinkSys Broadband router. I have no idea were to look for solution.

---

### Post by NikoC on 2007-03-31
This might sound stupid but have you unmarked the 'Work offline' option in the 'File' menu of mozilla? And second: can you access your routers homepage via mozilla?

---

### Post by linux_crazy on 2007-04-02
It is not 'Work offline' option I dug around and a source of problem is DNS.
When I change /etc/resolve.conf to 'nameserver 205.171.2.65
                                                        nameserver 205.171.3.65'

everything seems to work fine exept when I restart my system the resolve.conf
overwrites itself to original              'nameserver 192.168.0.1
                                                        nameserver 205.171.3.65'
and back to begining only konqueror works. Any ideas how to fix this problem???

P.S. getting tired changing resolv.conf

---

### Post by zvacet on 2007-04-03
If everything else is configured right go to the DNS tab and put your nameserver there>close.
```
pppoeconf
```

---

