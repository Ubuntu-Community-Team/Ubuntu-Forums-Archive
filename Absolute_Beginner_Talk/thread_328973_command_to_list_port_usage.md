---
title: "command to list port usage?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-12-31
I think there is a command that will list which processes are attached to which ports.  Anyone know what it is?  (not /etc/services, but a command that will list active processes)

---

### Post by moshuptrail on 2006-12-31
netstat - Google is so cool

---

### Post by pseudonym on 2006-12-31
What about one that lists the names of processes on ports not specified in /etc/services, and for which 'sudo netstat-ntlp' only shows something generic like 'python' or 'java'?...

---

### Post by Egeste on 2008-05-27
> **moshuptrail said:**
> I think there is a command that will list which processes are attached to which ports.  Anyone know what it is?  (not /etc/services, but a command that will list active processes)

```
sudo apt-get install nmap
nmap -p 1-65535 -sV 127.0.0.1
```

*Nmap ("Network Mapper") is a free and open source (license) utility for network exploration or security auditing. Many systems and network administrators also find it useful for tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running, what type of packet filters/firewalls are in use, and dozens of other characteristics. It was designed to rapidly scan large networks, but works fine against single hosts. Nmap runs on all major computer operating systems, and both console and graphical versions are available.*

---

