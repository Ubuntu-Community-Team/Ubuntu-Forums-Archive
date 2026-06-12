---
title: "Adept not communicating with server"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by BernieBBQ on 2007-12-03
Hi,

I cannot obtain the additional packages for Kubuntu 7.10 as Adept does not seem to be communicating with the Internet. I am fairly new at this. I have enable  the software sources, and tried both local and international. I have tried various sudo comands as suggested on several sites ... but I definitely do not seem to be connecting to the external server.

Similarly, Kmail does not send mail, it only receives it. I am confident of my settings and wonder if there is any common protocol issue.

Konquorer seems OK on the internet

---

### Post by vikram on 2007-12-03
> **BernieBBQ said:**
> Hi,

I cannot obtain the additional packages for Kubuntu 7.10 as Adept does not seem to be communicating with the Internet. I am fairly new at this. I have enable  the software sources, and tried both local and international. I have tried various sudo comands as suggested on several sites ... but I definitely do not seem to be connecting to the external server.

Similarly, Kmail does not send mail, it only receives it. I am confident of my settings and wonder if there is any common protocol issue.

Konquorer seems OK on the internet

do you have a firewall on ?

print the output of this command

sudo iptables -L

quick way to test firewall issues is

sudo iptables -F 
*warning* this will disable your firewall and is a security risk. use at your own risk and ensure you have your firewall up after testing.

---

### Post by BernieBBQ on 2007-12-08
Hi,

It does not appear to be a firewall issue

---

