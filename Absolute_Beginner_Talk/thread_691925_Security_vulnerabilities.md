---
title: "Security vulnerabilities"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-09
How to check in my system to know whether there is a security vulnerability, errors  or not?

---

### Post by randy78 on 2008-02-09
This can either be a lot of fun, or a nightmare, depending on you...

First, check out this security guide by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

You might want to read up on Bastille, Ossec, fail2ban, Denyhosts and hardening your IpTables configuration.

Then, after you get all set up, download some security scanning software such as Nmap or Nessus and do some different type of portscans against YOUR IP address to test for open ports and vulnerabilities.

Plus, grc.com has a great tool available called ShieldsUp to scan for open ports...

After that, just remember that security is a mindset and that the most dangerous thing to a computer system is the user.

Good luck
:popcorn:

EDIT: If you are using a hardware firewall, don't forget to harden those rules as well!

---

