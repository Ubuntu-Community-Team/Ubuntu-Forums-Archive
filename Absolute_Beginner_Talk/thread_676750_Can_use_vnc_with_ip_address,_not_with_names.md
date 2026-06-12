---
title: "Can use vnc with ip address, not with names"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Imsdal on 2008-01-24
I have a pretty much default setup of Gutsy on one computer and another one running Vista. I have enabled networking/sharing and installed vnc properly (all this is "as far as I can tell" only).

However, I can't use vnc with the computer names, only with ip addresses. This is the same in both directions. Both computers connect fine to the Internet.

Also, I can't share folders as neither computer can find the other. This may very well be related to the problem above.

How do I go about finding what has gone wrong?

---

### Post by wormser on 2008-01-24
This sounds like a DNS issue.  You can always test this by pinging by ip address and name.  You can add the names to you /etc/hosts file.  [Here]("http://www.faqs.org/docs/securing/chap9sec95.html") is more on it and some examples below.  To edit the file use **sudo nano /etc/hosts**.

208.164.186.1		deep.openna.com		 deep
208.164.186.2		mail.openna.com		  mail
208.164.186.3		web.openna.com		 web

---

### Post by Imsdal on 2008-01-24
> **wormser said:**
> This sounds like a DNS issue.  You can always test this by pinging by ip address and name.  

Strangely (to me, at least), "vncviewer 198.172.0.7" works, but "ping 198.172.0.7" doesn't. How could that be? This is from Ubuntu to Vista. From Vista, "ping 198.172.0.6" works.

My /etc/hosts is empty, save for the localhost references etc, but if ping doesn't work, that shouldn't be the issue, should it?

---

### Post by scorp123 on 2008-01-24
> **Imsdal said:**
> Strangely (to me, at least), "vncviewer 198.172.0.7" works, but "ping 198.172.0.7" doesn't. How could that be? This is from Ubuntu to Vista.  "ping" (echo reply) may be blocked (e.g. by Vista's firewall?). Simple as that :)

---

