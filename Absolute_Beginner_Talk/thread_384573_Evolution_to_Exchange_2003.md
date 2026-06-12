---
title: "Evolution to Exchange 2003"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by indianabeck on 2007-03-14
I'm trying to use Evolution to an Exchange Server. To test the URL on ubuntu, I go into Firefox and enter [http://www.beckb.com/exchange](http://www.beckb.com/exchange). It properly comes up with the OWA login dialogue and allows me to log in. OWA works like a charm

When I use the exact same URL in the Evolution setup and the exact same user and password, it says "Could Not Connect to Exchange Server"

I'm testing off the live CD.

---

### Post by mozkaynak on 2007-03-15
why do you use url address to get connected exchange server with evolution?
Evolution is a client and just enter proper smtp and mailserver addresses,
May be I completely misunderstand your problem.

---

### Post by indianabeck on 2007-03-15
Your solution would be fine if I wanted to use it as a POP server. Evolution gives you the ability to connect to an Exchange server as an Exchange server, there is a difference.

I think the issue is that Evolution expects form based authentication and SSL and will not work with standard windows authentication. Could someone familiar with Evolution using Exchange please respond?

Rather than using it as a POP server, I will just use OWA in FireFox if needs be.

---

