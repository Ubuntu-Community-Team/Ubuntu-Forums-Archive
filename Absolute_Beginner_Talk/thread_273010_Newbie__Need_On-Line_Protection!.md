---
title: "Newbie : Need On-Line Protection!"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by 7mm on 2006-10-07
Hi there, I've just started to use UBUNTU & it's Unique experience. So far I've Used Internet & I tell ya it's Fun. Though I'm little causious about Security so I want my system to be protected while I'm On-Line. Can you guys suggest me How to turn on the Firewall in UBUNTU, & if it isn't pre-installed  then how can I get one. Also, Do I need Anti-Virus for UBUNTU? I'm worried b'coz I'm Windows User switching to Linux. Please Help. Thank you.

---

### Post by zappa on 2006-10-07
There is a firewall included (iptables)
If you want to change some rules, install a GUI that can help you (firestarter)
IMHO AVscanners are a complete waste of resources :)

---

### Post by Linux Lover on 2006-10-07
I like guarddog.

to install guarddog, 

sudo aptitude install guarddog

---

### Post by 7mm on 2006-10-07
"zappa", If the Firewall is included then please tell me how can I activate it.

---

### Post by Linux Lover on 2006-10-07
Firestarter and Guarddog are both the frontend programs of your firewall. You may also activate it using terminal if you know what you are going to do. To do so, you may take a look over iptables. Just google over iptable and enjoy

---

### Post by zappa on 2006-10-07
To be clear, iptables is active from startup ;)
If you don't samba, use p2p or use your pc to connect to other pc's in your network and stuff like that, iptables is correctly configured as it is.

---

### Post by sbergman27 on 2006-10-07
> **zappa said:**
> To be clear, iptables is active from startup ;)
If you don't samba, use p2p or use your pc to connect to other pc's in your network and stuff like that, iptables is correctly configured as it is.

Not in Ubuntu, it's not.

```

root@voyager:~# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by kaplis on 2006-10-07
> **7mm said:**
> Hi there, I've just started to use UBUNTU & it's Unique experience. So far I've Used Internet & I tell ya it's Fun. Though I'm little causious about Security so I want my system to be protected while I'm On-Line. Can you guys suggest me How to turn on the Firewall in UBUNTU, & if it isn't pre-installed  then how can I get one. Also, Do I need Anti-Virus for UBUNTU? I'm worried b'coz I'm Windows User switching to Linux. Please Help. Thank you.

[http://www.brunolinux.com/07-Security/AV_Software_and_why_you_do_not_need_it.html](http://www.brunolinux.com/07-Security/AV_Software_and_why_you_do_not_need_it.html)

check this out;) 
and dont worry;)

P.s. i have Firestarter..but i dont use it at all. why? i dont know:mrgreen:

---

