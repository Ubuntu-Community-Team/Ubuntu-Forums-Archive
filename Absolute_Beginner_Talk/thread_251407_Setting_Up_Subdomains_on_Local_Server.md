---
title: "Setting Up Subdomains on Local Server"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by McKenna on 2006-09-05
I have installed Ubuntu as a test development server and I want to setup subdomains on the local server to test different sites. The hostname of the server is devserver so, for example, I am looking for site1.devserver to resolve as a site in Apache.

I have tried the solution [detailed here](https://help.ubuntu.com/community/LocalhostSubdomain), but it hasn't worked for me. I couldn't access the server by Hostname until I installed Samba so I'm wondering if that is related to the problem.

Anyways, if anyone has any ideas in relation to this I would be very grateful!

---

### Post by kidders on 2006-09-05
My understanding of DNS is that, in your example (site1.devserver) "site1" is the hostname, not "devserver". Make "devserver" your domain name and add aliases to your /etc/hosts for site1, site2, etc.

Of course, that approach probably won't cooperate if there are any other computers on your network. For that, you'd need a DNS server imo, so that other machines on your LAN know where to route packets.

---

