---
title: "Linux equivalent to Windows' hosts file"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-23
Hi,

What's the Linux equivalent of windows' hosts file?  Is it /etc/hosts.deny, and if so what's the syntax?  

I have a huge list of domains and IP addresses of spammers, scammers and the like which I want to automatically deny access to. 

On a similar note, what's a good, easy to configure, firewall for Linux?  

Thank you.

---

### Post by Bachstelze on 2007-01-23
It's just /etc/hosts :)

The standard firewall that comes with every Linux system is iptables. GUIs to configure id include Firestarted and Guarddog.

---

### Post by bionnaki on 2007-01-23
you shouldnt have to worry about spyware on linux...you shouldnt worry at all, actually. the only real reason to modify the hosts file is to block adverts, but this can be more efficient using adblocking in firefox or konqueror or whatever your primary browser is. you can also block spam with your email client, if you use one.

modifing the hosts file for the reason that windows-users do is somewhat a waste of time.

---

### Post by kosmic on 2007-01-24
> **bionnaki said:**
> you shouldnt have to worry about spyware on linux...you shouldnt worry at all, actually. the only real reason to modify the hosts file is to block adverts, but this can be more efficient using adblocking in firefox or konqueror or whatever your primary browser is. you can also block spam with your email client, if you use one.

modifing the hosts file for the reason that windows-users do is somewhat a waste of time.

I agree 100% with you :)

---

