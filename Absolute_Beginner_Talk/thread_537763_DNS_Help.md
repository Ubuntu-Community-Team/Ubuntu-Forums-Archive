---
title: "DNS Help"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by AutootuA on 2007-08-29
[SIZE="4"]*****NEWBIE ALERT*****[/SIZE]

I'm running Ubuntu Server 6.06 and I have just a basic installation. I followed  these [[COLOR="Blue"]instructions[/COLOR]]("http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu") to get it installed with Zimbra as well. Everything seems to be running fine, but I have a problem receiving emails. Emails go out with out a problem. I was told that it is a DNS problem but I don't have a clue how to fix it. Can anyone help? I've read and searched until I can't see straight. Any recommended tutorials would be appreciated! I hate being taken by the hand and shown the way but I'm desperate. 


Here is some info from my [[COLOR="Red"]SERVER[/COLOR]]("http://www.nunyad.biz"):

**/etc/hosts**

```
127.0.0.1       localhost.localdomain   localhost
192.168.254.160 mail.nunyad.biz mail

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

**host `hostname`**

```
mail.nunyad.biz is an alias for nunyad.biz.
nunyad.biz has address 67.141.183.82
mail.nunyad.biz is an alias for nunyad.biz.
mail.nunyad.biz is an alias for nunyad.biz.
nunyad.biz mail is handled by 10 67.141.183.82.
nunyad.biz mail is handled by 10 mailstore1.secureserver.net.

```

**dig mail.nunyad.biz mx**

```
; <<>> DiG 9.3.2 <<>> mail.nunyad.biz mx
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7741
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 2, ADDITIONAL: 3

;; QUESTION SECTION:
;mail.nunyad.biz.               IN      MX

;; ANSWER SECTION:
mail.nunyad.biz.        3600    IN      CNAME   nunyad.biz.
nunyad.biz.             3600    IN      MX      10 67.141.183.82.
nunyad.biz.             3600    IN      MX      10 mailstore1.secureserver.net.

;; AUTHORITY SECTION:
nunyad.biz.             3600    IN      NS      NS5.secureserver.net.
nunyad.biz.             3600    IN      NS      ns6.secureserver.net.

;; ADDITIONAL SECTION:
mailstore1.secureserver.net. 859 IN     A       64.202.166.11
NS5.secureserver.net.   2263    IN      A       208.109.78.180
ns6.secureserver.net.   1814    IN      A       208.109.80.75

;; Query time: 304 msec
;; SERVER: 166.102.165.11#53(166.102.165.11)
;; WHEN: Wed Aug 29 09:49:56 2007
;; MSG SIZE  rcvd: 203

```

---

### Post by deadgobby on 2007-08-29
[https://wiki.ubuntu.com/https%3a//help.ubuntu.com/community/DnsmasqHowto?action=show&redirect=KarlGoetz%2FDnsmasqHowto](https://wiki.ubuntu.com/https%3a//help.ubuntu.com/community/DnsmasqHowto?action=show&redirect=KarlGoetz%2FDnsmasqHowto)

---

### Post by AutootuA on 2007-08-29
> **deadgobby said:**
> [https://wiki.ubuntu.com/https%3a//help.ubuntu.com/community/DnsmasqHowto?action=show&redirect=KarlGoetz%2FDnsmasqHowto](https://wiki.ubuntu.com/https%3a//help.ubuntu.com/community/DnsmasqHowto?action=show&redirect=KarlGoetz%2FDnsmasqHowto)

I can not get the above link to work. I know I'm in trouble if I can't even follow a link. LOL

---

### Post by deadgobby on 2007-08-29
I click on the link and it work just fine.
:)
Gobby

---

### Post by Iowan on 2007-08-29
Doesn't work for me, either.  Searching for "DnsmasqHowto" yields:
https:/KarlGoetz/DnsmasqHowto
This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists. 
 "Existing pages with similar names" shows the above link.

---

### Post by AutootuA on 2007-08-29
After searching I found [[COLOR="Blue"]https://help.ubuntu.com/community/Dnsmasq[/COLOR]]("https://help.ubuntu.com/community/Dnsmasq"). I'm assuming this is the link I was suppose to go to.

---

