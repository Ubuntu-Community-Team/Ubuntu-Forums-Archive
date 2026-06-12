---
title: "[SOLVED] Ubuntu firewalled by default?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-14
Hi,

I have a fresh install of ubuntu feisty and I have installed mysql 5.0 using apt-get. I have the mysqld up and running fine and can connect to it from the local machine using the servername as localhost. However when I try to connect using the ssigned LAN ip address (192.168.0.5) I get ```
MySQL Error Nr. 2003 Can't connect to MySQL server on '192.168.0.5' (111)
```.

I also cannot connect from my windows machine although I can ping it fine.

Any ideas? Is there a firewall on ubuntu stopping me, or is it a mySQL configuration problem?

Thanks!

---

### Post by kavon89 on 2007-08-14
I am 90% sure it is. Both server edition and desktop edition have a firewall enabled by default. You need to tell it which ports you need open.

---

### Post by w4ett on 2007-08-14
You will need to manually modify your iptables (native firewall in ubuntu) OR install from the Synaptic Package manager the GUI frontend Firestarter.  In Firestarter you can control the open and closed arrangement of your iptables and set rules for them. See:

[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)

[http://www.ubuntux.org/how-to-install-the-firewall-firestarter](http://www.ubuntux.org/how-to-install-the-firewall-firestarter)

---

### Post by keymoo on 2007-08-14
Thanks I installed firestarter no problem. I then stopped the firewall and tried to connect again. Same error. I also put an entry in the firewall to allow 192.168.0.10 to connect (the machine that's trying to connect to MySQL). This shouldn't have made a difference though because the firewall is stopped.

I also checked the mySQL configuration and made sure that Disable Networking is unchecked  in the mySQL administrator.

I'm at a loss as to what else to check. I can ping 192.168.0.5 (where MySQL is located) fine from 192.168.0.10.

Any other ideas would be appreciated.

keymoo

---

### Post by w4ett on 2007-08-14
Firestarter is the GUI for iptables, turning it off does not affect the firewall operation it just makes it easier to control iptables.  Under the policy tab, have both incoming and outgoing port rules been added?

Also see:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

also:

[http://www.fs-security.com/docs/policy.php#outbound](http://www.fs-security.com/docs/policy.php#outbound)

---

### Post by fastpakr on 2007-08-14
Eh?  If you tell Firestarter to stop the firewall, it should just disable iptables.

---

### Post by w4ett on 2007-08-14
> **fastpakr said:**
> Eh?  If you tell Firestarter to stop the firewall, it should just disable iptables.


Yep you are right...If you disable it...I misunderstood..I thought he just quit Firestarter, which leaves the iptables running in the same status as before.

---

### Post by fastpakr on 2007-08-14
> **w4ett said:**
> Yep you are right...If you disable it...I misunderstood..I thought he just quit Firestarter, which leaves the iptables running in the same status as before.

You might be right - that would certainly explain him still getting those symptoms.

---

### Post by Hospadar on 2007-08-14
Try installing ssh on the machine that has mysql, can you ssh to the machine and then use mysql from there? (not that I suggest you use mysql that way, but it might help to diagnose the problem)

---

### Post by Alterax on 2007-08-14
Have you configured the MySQL permissions to allow remote access from users?

I ask this because I usually set these to only allow local logons with my machines (custom LAMP applications).

---

### Post by az on 2007-08-14
There is no firewall on a default Ubuntu install.  There just is nothing listening to the network by default.

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-719e91558dc00ee13c4549ae03444e7594a3d10b](https://help.ubuntu.com/community/ApacheMySQLPHP#head-719e91558dc00ee13c4549ae03444e7594a3d10b)

Set the bind address for mysql so that it listens to the network.

That's it.  No other funny business.

---

### Post by keymoo on 2007-08-14
az was right.

I bound MySQL to listen to my network address and all is fine. I was mislead by the checkbox which said Disable networking. At least MySQL is pretty secure out of the box!

Thanks everyone, what a great community you have here!

keymoo

---

