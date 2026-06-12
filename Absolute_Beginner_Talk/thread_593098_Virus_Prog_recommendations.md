---
title: "Virus Prog recommendations?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Disker on 2007-10-26
Is it needed and what would you recommend?  I have a dual boot Xp Pro and Gutsy new install so I want to make sure the Gutsy side of it is safe with email and any downloads I do whether they end up being used on the Gutsy or windows side.  Yes, I might download a windows prog using my Linux FTP client because it's faster.  

Thanks  :)

---

### Post by Crafty Kisses on 2007-10-26
> **Disker said:**
> Is it needed and what would you recommend?  I have a dual boot Xp Pro and Gutsy new install so I want to make sure the Gutsy side of it is safe with email and any downloads I do whether they end up being used on the Gutsy or windows side.  Yes, I might download a windows prog using my Linux FTP client because it's faster.  

Thanks  :)

You really don't need a virus program for Ubuntu, Ubuntu comes with built-in iptables, but if you must have one try ClamAV.

```
sudo apt-get install clamav
```

---

### Post by jon zendatta on 2007-10-26
virus is not an issue if you're using linux. but if you are communicating with windows, then 'firestarter' will ensure you do not infect those systems..

sudo apt-get update
sudo apt-get install firestarter

---

### Post by skymera on 2007-10-26
firesatrter just is a GUI for iptables which is the firewall..

try

ClamAV
AVG <--i found good, but waste of space

---

### Post by Crafty Kisses on 2007-10-26
> **skymera said:**
> firesatrter just is a GUI for iptables which is the firewall..

try

ClamAV
AVG <--i found good, but waste of space

Excatly. :)

---

### Post by erm4gh on 2007-10-26
The main reason for a anti-virus program under Linux is if you're sharing the files with Windows users. In your case where you're downloading files under Linux for Windows, why not make life simple and scan them when you switch to Windows? You don't gain much from scanning them earlier since any viruses can't do anything until you execute the files.

Rather than enabling a firewall under Linux, why not buy a router with a built-in firewall? You can frequently find them on sale for about $25. Unless you need to manage outbound connections that would also let you get rid of a firewall under Windows.

---

