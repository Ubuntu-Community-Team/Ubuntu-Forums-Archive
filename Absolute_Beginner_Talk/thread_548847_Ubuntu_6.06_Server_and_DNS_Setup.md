---
title: "Ubuntu 6.06 Server and DNS Setup"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by AutootuA on 2007-09-11
Can someone tell me if my server and my DNS settings are set up correctly? My server is just a basic setup, no LAMP setup. It will be used for a email server running Zimbra. 

**hostname**
```
mail.nunyad.biz

```

**/etc/hosts**
```
127.0.0.1       localhost.localdomain   localhost
67.141.183.84   mail.nunyad.biz mail

```

**host `hostname`**
```
mail.nunyad.biz has address 67.141.183.84

```

**dig nunyad.biz mx**
```
; <<>> DiG 9.3.2 <<>> nunyad.biz mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39437
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;nunyad.biz.                    IN      MX

;; ANSWER SECTION:
nunyad.biz.             3600    IN      MX      10 mail.nunyad.biz.

;; AUTHORITY SECTION:
nunyad.biz.             778     IN      NS      ns6.secureserver.net.
nunyad.biz.             778     IN      NS      ns5.secureserver.net.

;; ADDITIONAL SECTION:
mail.nunyad.biz.        3600    IN      A       67.141.183.84
ns6.secureserver.net.   3009    IN      A       208.109.80.75

;; Query time: 95 msec
;; SERVER: 166.102.165.11#53(166.102.165.11)
;; WHEN: Tue Sep 11 20:58:41 2007
;; MSG SIZE  rcvd: 133

```

---

### Post by AutootuA on 2007-09-11
Thanks anyway but I figured out my problem. All of the above was correct. My firewall had a port blocked that was causing my email problem. ):P

---

