---
title: "Godaddy link webserver to domain name"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-07-01
Hi,

I just purchased a domain name but am lost as to how to point the domain name to my home webserver.  I have a lynksis router and also use comcast cable modem.

Could someone advise me on how to link my home server to the domain name.

Thanks:D

---

### Post by Ek0nomik on 2007-07-01
This thread will hopefully help:

[http://ubuntuforums.org/showthread.php?t=408792](http://ubuntuforums.org/showthread.php?t=408792)

---

### Post by prostock3 on 2007-07-01
Thanks.  i saw this post.  I read somewhere that if i am behind a cable modem then i cannot have a static IP?  I configured my ubuntu to be static,  but what ip address do i use to link?  how can i find it?

thanks.

---

### Post by Ek0nomik on 2007-07-01
You should be able to get it to work by using your external IP address.

[http://whatsmyip.org/](http://whatsmyip.org/) - this should show you what it is.

Your external address is the address that the world sees you by, your internal (192.*.*.*) is what your household will see you as (or more properly, how people on your network will see you).

---

### Post by prostock3 on 2007-07-01
Thanks.  so when i set static

inside:
vi /etc/network/interfaces

does that mean the external turns static.or what exactly becomes static?

Thanks again.

---

