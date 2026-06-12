---
title: "who handles vmware security?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by munkyeetr on 2006-11-19
I am running VMWare Workstation (v5.5.2) with a Windows XP Pro client on an Ubuntu 6.06 host.

Do I need to be concerned with Windows security vulnerabilities? Should I be using Anti-virus and such inside the virtual machine? Is this necessary, or does Ubuntu handle the security?

The Windows client is accessing the internet through NAT, sharing the host IP address.:confused:

---

### Post by dmizer on 2006-11-19
yes ... your windows install under vmware can get infected.  your best bet is to use a good free antivirus (avast or avg) and make frequent image backups.  that way if your antivirus detects an infection, you can just restore your backup, rather than having to mess with the futility of cleaning an infected install.

your vmware windows will use the same firewall that your ubuntu machine does.  so, if you're using a router with a hardware firewall (best bet), then you'll be fine.  same with if you've insalled firestarter to configure iptables.

---

### Post by munkyeetr on 2006-11-19
thanx dmizer!

---

