---
title: "How can I add a DNS in Feisty?? THIS DOESN'T WORKS!!!!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-07-09
A fresh new Feisty 7.04.
I'm trying to setup my network card...
It's a mass guys...
Enable roaming... Static.... DHCP...
Well... I could set a static IP (that's what I wanted...)
Then... I try to set the DNS server... But I can't... Every time I hit the button (add) it deletes the address I just wrote...   
So... I can't surf or update my ubuntu...  

My ethernet card is well connected cuz I can ping my gateway... 
The only thing I need to do now is go configure my DNS...  There is any other way to do it? 
Network manager sucks....    (Sorry guys.. but I'm angry...) 

Thank you mates.

---

### Post by FleetAdmiral74 on 2007-07-09
When you type in the IP for the DNS, hit enter.

---

### Post by Kosimo on 2007-07-09
> **FleetAdmiral74 said:**
> When you type in the IP for the DNS, hit enter.

Done...
Doesn't works... :(  
It looks like is a bug...

Any other way to put it from the terminal?

---

### Post by hyper_ch on 2007-07-09
I think the dns servers should be stored in

```

/etc/resolv.conf

```

not 100% sure but have a look at it.

---

### Post by zvacet on 2007-07-09
When you add DNS try to click few times.If I remember correctly all address will become orange.It is not bug, just don´t lose patientce.

---

### Post by tcpip4lyfe on 2007-07-09
> **hyper_ch said:**
> I think the dns servers should be stored in

```

/etc/resolv.conf

```

not 100% sure but have a look at it.

It is.  try this:

```
gksudo gedit /etc/resolv.conf
```

This is what mine looks like:

> search ats.mcleodusa.net
nameserver 192.168.0.1
nameserver 192.168.0.1
nameserver 192.168.0.1

---

### Post by hyper_ch on 2007-07-09
it's the /etc/resolv.conf file... add you nameservers in this format:

```

nameserver 192.168.0.1
nameserver 192.168.0.2
nameserver 192.168.0.3
....

```

---

### Post by Carlos Santiago on 2007-07-09
sudo nano /etc/resolv.conf

---

### Post by webdr on 2007-10-11
I just finished testing this (sudo gedit /etc/resolv.conf) on a desktop install and it works properly.

Then for grins and since I was loading a feisty server install onto an armada laptop via PXE (learning pxe / netboot installs has been a bit of a trick.) I tried it on the freshly installed server and indeed it doesn't work.

Anyone have any thoughts about further diagnostics or solutions?


:confused:

---

