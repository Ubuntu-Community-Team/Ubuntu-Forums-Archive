---
title: "Ethernet connectivity problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ringorulesall on 2007-06-17
Hi, 

Im new to Linux experienced windows user (Like many people here). I have a compaq presario with the broadcom 54g. I am also running the x64 build of ubuntu in a dual boot setup with xp. I searched the forums and found out that there are all sorts of problems with the broadcom, but the first step was to gain an internet connection. So I plugged in the Ethernet and everything worked fine.

I then went to the forums, and 3 min. later and I had no internet connection. Restart, try again and nothing. 

Im able to access my router/modem, which is an actiontec (I know... *cringes*) 54g, but in the active user list it shows my laptop as "Unknown" where it should show the computer name. So i figured that it was my router. Just to be sure I opened up the terminal and pinged google.com, But I was able to connect and there were no packets lost. There was however a high response time of 189ms (Im on 1.5mb/s DSL). 

I'm still not sure if its my router or Ubuntu or both,
Any suggestions?

---

### Post by candtalan on 2007-06-17
I am no expert, but if you get out to google with ping but other things are not good it may be related to your domain name server settings (DNS). Your machine and connection will be using a DNS somewhere to translate from the text domain name to the final IP address.
Your settings would usually point to the DNS of your ISP, but I think youi could use others (?)

hth

---

### Post by Gimpy_Rob on 2007-06-17
If you are reaching google.com with the name google.com, then DNS is fine.  Double check to make sure it isn't just a DNS cache somewhere.  maybe post result of ```
cat /etc/resolv.conf
```

---

### Post by EdThaSlayer on 2007-06-17
> **candtalan said:**
> I am no expert, but if you get out to google with ping but other things are not good it may be related to your domain name server settings (DNS). Your machine and connection will be using a DNS somewhere to translate from the text domain name to the final IP address.
Your settings would usually point to the DNS of your ISP, but I think youi could use others (?)

hth

You can check if it is the DNS that is at fault. Just try going to this site [http://www.opendns.com/](http://www.opendns.com/) and getting the DNS adresses that they give. :p

---

### Post by ringorulesall on 2007-06-17
INPUT: Cat /etc/resolv.conf

OUTPUT:
Search Domain actdslmp
nameserver 192.168.0.1
nameserver 205.171.3.65 (Old DNS)

I then changed the prepend line

INPUT: sudo /etc/init.d/networking restart

OUTPUT: DHCPDiscover on eth1 to 255.255.255.255 port 67:Network is down
No DHCPOffers recieved

---

