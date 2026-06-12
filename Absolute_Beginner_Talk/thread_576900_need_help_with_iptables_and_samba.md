---
title: "need help with iptables and samba"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-10-15
I would love if someone could help me write some iptables rules to do the following:

allow ping and samba file sharing between my laptop(windows) and Desktop(ubuntu fiesty) none of the guides I have found here work.  the HOWTO at [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111) definitely does not work for me, though it lookesd promising, I think it is obsolete.  The part to create a daemon works, but the script gives errors and the services arent allowed after running it.

I have a DHCP environment to work in and my roomate might have problems with setting up static-ips so i'd rather try to validate using hostnames or mac addresses.

---

### Post by update_manager on 2007-10-15
> **Jive Turkey said:**
> I would love if someone could help me write some iptables rules to do the following:

allow ping and samba file sharing between my laptop(windows) and Desktop(ubuntu fiesty) none of the guides I have found here work.  the HOWTO at [http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111) definitely does not work for me, though it lookesd promising, I think it is obsolete.  The part to create a daemon works, but the script gives errors and the services arent allowed after running it.

I have a DHCP environment to work in and my roomate might have problems with setting up static-ips so i'd rather try to validate using hostnames or mac addresses.

This might work, although it might be easier for them to use ftp (windows can use ftp folders as mapped drives I think).

#!/bin/bash
iptables -F

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD REJECT

iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -p tcp -m state --state NEW,INVALID -j LOG
iptables -A INPUT -p tcp -m state --state NEW,INVALID -j DROP

iptables -A INPUT -p icmp -m limit -limit 10/second  -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 137:139 -m mac --mac-source <MAC> -j ACCEPT
iptables -A INPUT -p udp -m udp --dport 445 -m mac --mac-source <MAC> -j ACCEPT
iptables -A INPUT -p udp -m tcp --dport 445 -m mac --mac-source <MAC> -j ACCEPT

Save it in a file, then run (command line) 

chmod +x <filename>
sudo ./ <filename>


If it works, then put the file you chmod'd in /etc/rc.local so it will get loaded at boot.

If this is too complicated, you could use firestarter or [http://www.shorewall.net/MAC_Validation.html]("http://www.shorewall.net/MAC_Validation.html")l.

---

### Post by Insightfill on 2007-10-16
> **update_manager said:**
> This might work, although it might be easier for them to use ftp (windows can use ftp folders as mapped drives I think).

Windows will keep recent FTP connections in your "My Network Places" section in Windows Explorer, but won't let you map to it.  Novell made a product that allows Windows to map FTP shares, free for student use, but pay for commercial I think.  Still: for simple file transfer, FTP may be enough.

You can also use a product like WinSCP which will keep a local Windows folder in sync with a remote Linux SFTP/SCP share.

But: for simply mapping a drive and using the remote files in real-time, SMB works fine.  I've got a Windows, Mac and Linux machine all happily using the Samba share on Ubuntu in the basement.

---

### Post by update_manager on 2007-10-20
A more version that would just accept all traffic from the specified mac addresses should look like:

#!/bin/bash
iptables -F

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD REJECT

iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW,INVALID -j LOG
iptables -A INPUT -p tcp -m state --state NEW,INVALID -j DROP

iptables -A INPUT -p icmp -m limit -limit 10/second -j ACCEPT

iptables -N PRIV_MACS
iptables -A PRIV_MACS -m mac --mac-source <mac1> -j ACCEPT 
iptables -A PRIV_MACS -m mac --mac-source <mac2> -j ACCEPT 
iptables -A PRIV_MACS -m mac --mac-source <mac3> -j ACCEPT

---

