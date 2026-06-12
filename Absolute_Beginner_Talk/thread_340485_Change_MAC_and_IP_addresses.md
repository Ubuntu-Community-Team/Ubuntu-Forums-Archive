---
title: "Change MAC and IP addresses"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2007-01-17
Can someone share a detailed explanation of how to change a MAC and IP addresses is Ubuntu?
I need to know very badly, thanks in advance.

---

### Post by JamieC on 2007-01-17
You can change your MAC address (at a software level, not a hardware one) by using a new terminal to run the following (where <device> is the name of your network interface and <address> is the new address):
```

sudo ifconfig <device> down
sudo ifconfig <device> hw ether <address> 
sudo ifconfig <device> up

```

I think the best you can do to renew your IP address is to send a DHCP request by using dhclient. Open a new terminal and run the following (where <device> is the name of your network interface):
```

dhclient <device>

```

---

### Post by irish_flu on 2007-01-17
To change your IP address in Gnome, go to System --->Administration ---> Networking.  Click on (highlight) the connection you wish to change (for example "wired connection") and then click "Properties".

If it is set to "Automatic Configuration (DHCP)", then you're getting an address automatically.  If you need to change it to a specific IP address, select "Static IP Address" and there you'll be able to enter a new IP for the machine.

The MAC address does not get changed, it's hard-coded into your network card.  It can be "spoofed", but if you don't know what that is you probably don't want to do it.

---

### Post by Ben Sprinkle on 2007-01-17
HideMyMac for Windows seems to work. I just need to 'hide or make it look different to my router'.

---

### Post by Patrick-Ruff on 2007-01-17
for some reason, edgy has a screwed up shortcut for Networking . . . it doesn't run with GKsudo.

I recommend you do the command-line way.

---

### Post by irish_flu on 2007-01-17
> **Patrick-Ruff said:**
> for some reason, edgy has a screwed up shortcut for Networking . . . it doesn't run with GKsudo.

I recommend you do the command-line way.

I think the original Poster is a Dapper user.

My shortcut in Edgy seems to work fine.  I've upgraded from Dapper though, not installed fresh....

---

### Post by Ben Sprinkle on 2007-01-17
```

 Join Date: May 2006
Beans: 883
Ubuntu 6.06 Dapper User 

```
;)

---

