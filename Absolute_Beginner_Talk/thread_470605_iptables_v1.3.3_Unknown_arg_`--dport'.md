---
title: "iptables v1.3.3: Unknown arg `--dport'"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-06-11
Hi

I'm trying to close port 53 using:

iptables -I INPUT --dport 53 -j DROP

But I keep getting:

iptables v1.3.3: Unknown arg `--dport'

Any suggestions as to what I'm doing wrong;)

Ward

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]Not really sure, but I looked at the man page, and I think you might need to specify -p dccp in order to use the --dport argument. [/COLOR]

---

### Post by Wardazo on 2007-06-11
... and the error message dissapeared.

Thanks

---

### Post by steve.horsley on 2007-06-11
I'm not sure that dccp is the right protocol to specify. I think you should be specifying -p udp and -p tcp (two separate lines needed) to block DNS over UDP and DNS over TCP.

---

### Post by Wardazo on 2007-06-11
You are of course right. -p udp and -p tcp on two separate lines.

Thanks

Ward

---

