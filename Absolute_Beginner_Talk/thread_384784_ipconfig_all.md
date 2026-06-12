---
title: "ipconfig /all"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by j0eb0b on 2007-03-14
i have searched the forum and found various answers to the ipconfig question.  Is there a linux command equivalent to ipconfig /all in Windows?  I want to see my assigned IP address, default gateway and DNS servers.

Thanks,
joe

---

### Post by jkeyes0 on 2007-03-14
use the following text in Terminal
```
ifconfig
```

---

### Post by j0eb0b on 2007-03-14
ifconfig shows me my locally assigned IP but not the default gateway or DNS servers.  Is there a switch i need to add?

Thanks,
joe

---

### Post by irwa82 on 2007-03-14
hi,

/sbin/route -n --- This will show you what the default routes are on the system. the -n shows ip instead of hostnames.

cat /etc/resolv.conf --- this will show you what the dns your system is using.

---

### Post by j0eb0b on 2007-03-14
Sorry to be a bit of a dolt.  Can you show me an example of the full command syntax to dispaly path and DNS servers?  I understand the path statements you quoted but are these appended to the ifconfig command?

Thanks, joe

---

### Post by jkeyes0 on 2007-03-14
what he meant, I believe, was to go to terminal and type
```
cat /etc/resolv.conf
```
and
```
route -n
```


cat /etc/resolv.conf will read something like
```
nameserver X.X.X.X
```
where X.X.X.X is the IP address of your DNS server

and route -n should show the routing table, including your gateway route.

---

