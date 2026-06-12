---
title: "What is my internal IP address?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-07-20
What is my internal IP address?

---

### Post by TripleE on 2006-07-20
> **IDontKnow9998 said:**
> What is my internal IP address?

127.0.0.1 will be your internal ip address.  If you have a router, you will probably have a 192.168.x.x IP.  You can do a the following to check your ip address from the terminal.
```
ifconfig
```

---

### Post by IDontKnow9998 on 2006-07-20
> **TripleE said:**
> 127.0.0.1 will be your internal ip address.  If you have a router, you will probably have a 192.168.x.x IP.  You can do a the following to check your ip address from the terminal.
```
ifconfig
```

ok tnx... how would I change my ip address? I am using a router and I want it to be 192.168.1.10

edit: NM I got it working....

---

### Post by scxtt on 2006-07-20
type **network-admin** into a terminal window and set a static IP ...

---

### Post by IDontKnow9998 on 2006-07-20
> **scxtt said:**
> type **network-admin** into a terminal window and set a static IP ...

I got it to work with the network tools (Had missed that useful tool first time around somehow)

---

