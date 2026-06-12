---
title: "localhost connection refused"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Storyman on 2006-12-09
I have been unable to establish a connection to localhost in firefox.  The problem first came about when I tried starting phpmyadmin.  I have tried entering 127.0.0.1 instead of localhost, I have tried editing the /etc/hosts file, I have tried removing phpmyadmin and just putting a test html file in /var/www, I installed nmap and ran to see which ports are open, but it doesn't show port 80 as being open, and I have tried opening port 80 on my dlink di-624 router, all to no avail.  Any ideas?

---

### Post by taurus on 2006-12-09
What does your /etc/hosts look like then?

```
cat /etc/hosts
```

---

### Post by Storyman on 2006-12-09
cat /etc/hosts brought this:

127.0.0.1 localhost sonykelsey


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Storyman on 2006-12-10
I can also ping both localhost and 127.0.0.1 successfully.

---

### Post by Storyman on 2006-12-14
Yes I am a newbie, you have to have apache2 installed and running, so even though I don't have phpmyadmin running yet, at least I can get to the apache default page when I type in "localhost"

---

