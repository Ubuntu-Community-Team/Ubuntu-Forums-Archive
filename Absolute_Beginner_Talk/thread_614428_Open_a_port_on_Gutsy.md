---
title: "Open a port on Gutsy"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by kamasabi on 2007-11-15
howdy fellas,

   I'm trying to figure out how to open a couple specific ports on my file server.  they are 32976 and 12975.  I want to open these so I can use a vpn, hamachi, properly.  I tried these commands to open the ports to no avail.

sudo iptables -A FORWARD -p udp -m -udp --dport 32976 -j ACCEPT
sudo iptables -A FORWARD -p tcp -m -tcp --dport 12975 -j ACCEPT

Is there something I am forgetting to do prior or something wrong with what I typed?

Thanks in advance,

Kama

---

### Post by ramjet_1953 on 2007-11-16
You may want to try installing Firestarter. It is a graphical GUI for iptables.

Just makes things a little easier.

> [COLOR="Red"]sudo apt-get install firestarter[/COLOR]

Regards,
Roger :cool:

---

### Post by Inxsible on 2007-11-16
+ 1 on Firestarter. Makes it very easy to open ports

---

### Post by kamasabi on 2007-11-16
I tried it once before, but it didn't work -_-.  Here is how I had it set up with firestarter:

Internet device = eth0
IP address is assigned via DHCP

Enable Internet connection sharing
Lan device = Unknown device (ham0)  (hamachi virtual device)

_Policy_

**_Inbound Traffic Policy_**

**HTTPS**
443
everyone

**Hamachi**
12975
everyone

**Hamachi**
32976
everyone

**Samba (SMB)**
137
everyone

**Samba (SMB)**
138 
everyone

**_Outbound traffic policy_**
Permissive by default, blacklist traffic

if you need more info or my iptables.rules, let me know.

Thanks, 

Kama

---

