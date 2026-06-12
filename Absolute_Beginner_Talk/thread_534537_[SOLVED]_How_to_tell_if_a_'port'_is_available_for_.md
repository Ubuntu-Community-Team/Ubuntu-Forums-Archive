---
title: "[SOLVED] How to tell if a 'port' is available for azureus"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-25
According to the Azureus Wiki page: NAT problem:

Port Forwarding on Linux, specifically Ubuntu
[http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu](http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu)

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


Your configuration change will then persist through reboots. 

Other than the file created, where can I look or how can I test to see if the port I chose (64000) is open? running the NAT test in azureus always returns a timed-out error after 20 seconds. And (stupidly, I suppose) does the number 64000 need to be seen in the file as: <64000> ?

---

### Post by Mark_in_Hollywood on 2007-08-25
After more gimcrackery coding with azureus, the problem has resolved itself, and I dont' know what I did or changed that would have mattered.

---

