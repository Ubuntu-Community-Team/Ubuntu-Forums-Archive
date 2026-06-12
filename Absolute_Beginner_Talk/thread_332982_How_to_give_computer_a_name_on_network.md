---
title: "How to give computer a name on network"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-01-06
I can see the computer connected to my router, no problems there but its device name is unknown.

Anyone know how I can change this and give my computer a name?

---

### Post by xiaoxin on 2007-01-06
go to **System -> Administration -> Networking**
then **Network settings**

**General Tab -> Host Settings -> Hostname** here specify the computer name

---

### Post by kinematic on 2007-01-06
it's much faster to type "sudo hostname nameyouwant" in a terminal ;)

---

### Post by moshuptrail on 2007-01-06
I have the same issue.  I have the host name set.  I can doublecheck it in /etc/hostname and it's there too.  BUT, the router doesn't seem to pick it up.  It shows "unknown".  I think that's what the original poster is asking about.

It's important if you want to set up semi-static IP addresses in the router.

---

### Post by Bachstelze on 2007-01-06
You might reed to restart your interface :

```
sudo ifdown eth0 && sudo ifup eth0
```

also, make sure you edit /etc/hosts with the new hostname or you won't be able to sudo.

---

### Post by Jareth on 2007-01-07
Yeah moshuptrail, thats whats happening. It just says unknown in the router config.

I also noticed that some of the other computers don't appear in attached devices, but occasionaly they do.

Bit of a mystery all round.

---

### Post by WirelessMike on 2007-02-12
Surefire fix to make your computer's name show up in your router when you boot (k)ubuntu:

> sudo nano /etc/dhcp3/dhclient.conf

find this line:
#send host-name "";

remove the # and put the machine name of your choice in the quotes.

further down there is another line to edit:
# option host-name "";

do the same thing here then save and exit.


That's it.  Cycle your connection (ifconfig eth0 down; ifconfig eth0 up) and your router, whatever kind it is, will find your machine name automagically when your machine reacquires it.  This change is "sticky," so you don't have to edit the file every time you reboot or edit a startup script.  It's my favorite kind of edit--  One shot, done!

---

### Post by trav5 on 2007-02-12
> **WirelessMike said:**
> Cycle your connection (ifconfig eth0 down; ifconfig eth0 up) and your router, whatever kind it is, will find your machine name automagically when your machine reacquires it.

Works GREAT! Thanks Mike. I had to reboot because I could not power down my router at the moment. 

Have some:popcorn:

---

