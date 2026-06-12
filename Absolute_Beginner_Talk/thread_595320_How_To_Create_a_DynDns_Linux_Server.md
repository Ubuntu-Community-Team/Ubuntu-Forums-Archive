---
title: "How To: Create a DynDns Linux Server"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mattc908 on 2007-10-28
Hey guys and girls, I know a lot of people want a step by step guide on how to set up a FTP server using DYNDNS. Well I set up an easy guide on how you can. Just for kicks I hosting the guide on the server I created by using the guide I built. I test the steps to make sure they work! Let me know what you guys think. This guide is VERY step by step, and very simple. 


Guide:
[http://mattc908.dyndns.org/forum/viewtopic.php?t=5](http://mattc908.dyndns.org/forum/viewtopic.php?t=5)

---

### Post by kidders on 2007-10-29
Hi there,

Just a comment, really...

I would very strongly advise against publicly exposing an FTP server on a machine pointed to by a dynamic DNS service. Ignoring the fact that FTP is unacceptably insecure at the best of times, DDNS subscriptions usually attract malicious activity like moths to a flame.

Unless carefully handled, following your howto could expose a user's entire network ... I suggest adding a prominent warning to that effect, or perhaps describing the setup procedure for something a little safer (eg SFTP or FTPS).

---

