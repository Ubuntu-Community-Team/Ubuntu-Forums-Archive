---
title: "Sharing HOSTS or Aliases over network"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-07-10
Greetings, I am on a wireless network, and I was wondering if there was some way to share my HOSTS or Alias from "Network Settings" over the network.

Example: I go to Network Settings > Hosts.
I make a new alias for my IP, and I make it 56.lan.
So, how would everyone else on the network be able to access 56.lan ?

I don't know if this is possible or not anyhow.
Any ideas would be helpful :)

Dr Small

---

### Post by PgR on 2007-07-10
I'd either give them a copy of your hosts file (/etc/hosts) or set up a dns server.

if you decide to distribute the hosts file, then linux boxes should have it as /etc/hosts and windows boxes as c:\windows\system32\drivers\etc\hosts (or c:\winnt if that's where windows is installed.)

---

### Post by Dr Small on 2007-07-10
How would I setup a DNS server?

---

### Post by PgR on 2007-07-11
Not done that myself in Ubuntu - but here's a write-up by someone who has!

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

