---
title: "Join to Active Directory"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by WElliott on 2007-05-29
I have configured my samba, winbind & nsswitch configs as found in early posts. After restarting services I try the "net ads join administrator" and receive the following;

[2007/05/17 08:47:23, 0] utils/net_ads.c:ads_startup(289)
ads_connect: Invalid or incomplete multibyte or wide character

I have not been able to find anything on this in the forum. What did I do wrong?

Thanks!

---

### Post by rgraves22 on 2007-05-30
From the win networking side of things, Are you trying to add it to a domain at work? If so, there is probaly a GP that prohibits that from happening..

Im running my laptop at work, its hooked into a switch, and I can navigate to servers and my desktop, but I'm also a domain admin.. so I have the privlages to do so.

---

