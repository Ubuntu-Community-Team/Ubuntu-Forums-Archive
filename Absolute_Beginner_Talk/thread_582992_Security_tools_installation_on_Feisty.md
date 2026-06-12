---
title: "Security tools installation on Feisty?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by renegade_0503 on 2007-10-20
I recently installed Ubuntu Feisty (desktop version) on my dual-boot system (the other OS is Win XP).
I wanted to know if I can connect the ethernet cable to the system without installing additional security tools like how we usually do it in Windows. From the Ubuntu security forum, it looks like someone has recommended Knoppix-STD (Security Tools Distribution,  [www.knoppix-std.org](www.knoppix-std.org)) since it has open-source security and intrusion-detection utilities; password crackers, packet sniffers, port scanners, WEP crackers, encryption utilities, firewall and anti-virus software, etc. etc. but at the same it was also mentioned that the default Ubuntu installation opens zero ports to the outside world, so a firewall is redundant. That's a little confusing. 

Any clear direction?

---

### Post by mikeyphi on 2007-10-20
"the default Ubuntu installation opens zero ports to the outside world, so a firewall is redundant."
From what I've read - that's true for a personal Ubuntu installation. Firewall is usually only suggested for Server installations.

---

### Post by Paqman on 2007-10-20
Absolutely. The default install is secure.

There's no need to install antivirus software on a desktop. Ubuntu has a built in firewall (called iptables) A good GUI for configuring it is Firestarter, which is in the repos.

---

