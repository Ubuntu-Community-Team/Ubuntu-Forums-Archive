---
title: "torrent"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Ramrod_The_Wizard on 2007-11-04
H

---

### Post by Ramrod_The_Wizard on 2007-11-04
Oops, sorry accidental post.

Well down to what i was going to ask...
I'm currently using azureus and i try to open the auto-firewalled ports, but when i put in the commands in root terminal it says there is a syntax error.

Btw the commands I put in were..
iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

---

### Post by Ramrod_The_Wizard on 2007-11-04
What am I doing wrong?  I went into root terminal and the same problem persists.

---

### Post by Maestro23 on 2007-11-04
Might help. IPTables How-To: [https://help.ubuntu.com/community/IptablesHowTo?highlight=%28tables%29%7C%28ip%29](https://help.ubuntu.com/community/IptablesHowTo?highlight=%28tables%29%7C%28ip%29)

---

### Post by Ramrod_The_Wizard on 2007-11-04
Someone said firestarter is what I need to look at.  Is it a firewall itself or a firewall manager?

Also, how to i open my ports using firestarter?

---

### Post by zippy028 on 2007-11-04
I believe firestarter is simply a gui for iptables. You can install it via synaptic or through terminal 
```
sudo apt-get install firestarter
``` 
I am not an expert with this program but I believe it has a wizard that will allow you to setup access restrictions and exceptions for common services.

John

---

### Post by Maestro23 on 2007-11-04
> **zippy028 said:**
> I believe firestarter is simply a gui for iptables. You can install it via synaptic or through terminal 
```
sudo apt-get install firestarter
``` 
I am not an expert with this program but I believe it has a wizard that will allow you to setup access restrictions and exceptions for common services.

John

Correct.  Just a GUI for managing the IP-Tables. Website link below(FAQ, Documentation, etc...)

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by daengbo on 2007-11-05
You probably need to replace "<your port number>" with something like "6881:6889"

Do you have a firewall running? If you don't, you won't need to use those commands. Ubuntu doesn't run a firewall by default, since it doesn't have any open ports.

---

### Post by dfreer on 2007-11-05
> **Ramrod_The_Wizard said:**
> 
Btw the commands I put in were..
iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

Same as above. **<your_port_number>** should not be entered literally, you should replace it with the port number/s you wish to use. This is what mine looks like:
```

iptables -I INPUT -p tcp --dport 51000:52000 -j ACCEPT
iptables -I INPUT -p udp --dport 51000:52000 -j ACCEPT

```

The main thing here, if you are behind a home router using NAT, is to:
(1) Decide what port numbers you want to use, in a range.
(2) Set up an static IP address for your machine.
(3) Forward those ports from your router (if you have one) to your machine's static IP.
(4) If you are running firewall software on your machine (as said above, by default you aren't), open up the ports in the iptables firewall (firestarter is just a GUI frontend for this firewall) by entering the above two commands, replacing the port numbers with the port numbers you specified earlier
(5) Make sure azureus is using the same port numbers in it's configuration.

The above is really only for home router w/NAT situations, you'll need to do it differently if your network is not setup like this.

---

