---
title: "How to do this on Ubuntu?"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-07
Hello guys, I have a list of a question here:

1. How could we find out our IP such as the ipconfig command in Windows?
2. How do we do a "ping" and "tracert" in Ubuntu? How do we find out how fast our connection is (if it is at all possible)?
3. How could we do a "ipconfig -release" and "ipconfig -renew" such as in Windows?

Is there any kind of HOWTOs (besides Ubuntuguides.org) and tutorial on networking with Ubuntu?

Thanks

---

### Post by Lord Illidan on 2005-07-07
How about this? 
[http://rak.isternet.sk/linux-netman/commands.html](http://rak.isternet.sk/linux-netman/commands.html)

---

### Post by nocturn on 2005-07-07
[QUOTE=ozzie123]Hello guys, I have a list of a question here:

1. How could we find out our IP such as the ipconfig command in Windows?
2. How do we do a "ping" and "tracert" in Ubuntu? How do we find out how fast our connection is (if it is at all possible)?
3. How could we do a "ipconfig -release" and "ipconfig -renew" such as in Windows?

Is there any kind of HOWTOs (besides Ubuntuguides.org) and tutorial on networking with Ubuntu?

Thanks[/QUOTE]

ifconfig does it.   A release is done by dhcpcd I think (try man dhcpcd or man dhclient).

ping exist on Linux, as wel as traceroute.

---

### Post by ozzie123 on 2005-07-07
Hey found it working!

Thank you guys ;-)

---

