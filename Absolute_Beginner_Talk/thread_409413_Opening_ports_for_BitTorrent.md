---
title: "Opening ports for BitTorrent"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-14
I seem to be getting NAT errors (whatever they are) using Azureus. The Wiki says this:

> Port Forwarding on Linux, specifically Ubuntu

Firstly the earlier notes on port forwarding for your router apply as before. Computers running Ubuntu, by default, come with all the ports locked down and you need to open the ports in ubuntu by using the iptables command. Other flavours of linux behave similarly

The commands below can be entered in a root terminal session to open the ports (TCP and UDP)

iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

<your_port_number> is the port number you have used for port forwarding (Avoid 6881-6999, any from 49125-65535 is fine)

Once you've established the port is open you need to make the change persist through a reboot

      create a file /etc/init.d/iptables_azureus and add the lines below
        (sleep 220
         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) &

The (sleep 220 is there to make the script wait a few minutes to allow subsequent firewall configuration scripts to run. 220 seconds is a large value and you may choose to configure a lower value. The key is that the opening of the azureus port is not countermanded by the firewall initialisation which runs later. At the end is a ) & which allows the script to let the rest of the boot continue, while the script waits.

   chmod +x /etc/init.d/iptables_azureus make the file executable
   update-rc.d iptables_azureus start 51 S . links the file into the startup sequence


Your configuration change will then persist through reboots. Further info on the startup process in this ubuntu howto 

but I don't know what number I'm supposed to put in <your_port_number> - how do I find my port number (or do I just make it up)?

Also it says a root terminal session - what is that? I know what Terminal is but how do I make it a Root session?

---

### Post by Seisen on 2007-04-14
Are you using IPtables, a router or both. Let us know so we can figure out the problem.

---

### Post by swey on 2007-04-15
> **Seisen said:**
> Are you using IPtables, a router or both. Let us know so we can figure out the problem.

I do have a router (Linksys) and its a Virgin (NTL) broadband account using a cable modem. I don't have this problem on my Win PC though so it seems to be Ubuntu related accordingto the Azureus FAQ. Don't know what IPtables are

---

### Post by xpod on 2007-04-15
Install "firestarter" for an easy way to set your firewall rules etc.

It`s a graphical frontend for iptables and a lot easier to get the head round:D

---

### Post by swey on 2007-04-15
I just tried that but it didn't work and now my network isn't working either :( None of my smb shared folders are showing up on my Windows PC's.


edit - restarting samba in terminal fixed it but I've turned the firewall off

---

