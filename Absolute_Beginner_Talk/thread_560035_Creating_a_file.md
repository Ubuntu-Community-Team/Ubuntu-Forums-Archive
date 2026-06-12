---
title: "Creating a file?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by OisinT on 2007-09-25
I need to create a file to run everytime I start the machine.  Basically this is what I need to do, but I'm not sure exactly how to do this in the terminal.

> Once you've established the port is open you need to make the change persist through a reboot

  [script]    create a file /etc/init.d/iptables_azureus and add the lines below
        (sleep 220
         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) & [/script]
[script]

   chmod +x /etc/init.d/iptables_azureus make the file executable
   update-rc.d iptables_azureus start 51 S . links the file into the startup sequence [/script]


thanks in advance

---

### Post by Dr Small on 2007-09-25
why not just use firestarter to open ports ?

---

