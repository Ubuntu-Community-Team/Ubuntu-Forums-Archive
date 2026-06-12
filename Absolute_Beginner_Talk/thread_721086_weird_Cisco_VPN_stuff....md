---
title: "weird Cisco VPN stuff...?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by etothepi on 2008-03-11
Okay, I've made a few posts today, one of which was a terrible frustrated tirade.  That has been my low point, and I'm mildly sorry for it.

But - the VPN is still not going.

I'm using vpnclient.  I am not sure what the "group name" should be, but I think it should be University of Arizona.  I connect to the correct IP address.  There is something about connecting to the proper TCP or UDP port, I can't remember which one it is (nor find it now, of course), but it is either 1000 or 10000.  I evidently don't have the required group password, but can get it.  It's probably half my problem.

But when I try to connect to it, not only does it not connect, but my entire "connection" icon in the status bar disappears,  I'm not sure where else I can find this line of information to try to correct things, nor why exactly it's doing it.  I still have connection when it disappears, so I'm kind of lost on it.  I will try getting the group password and trying that (which I've just thought of), and if that works, I'll close the thread, but if not I'll write and hopefully get good thoughts.

---

### Post by Rocket2DMn on 2008-03-11
Hey man, don't get discouraged.  Here is a link to a post I followed last summer to get my vpn client working - [http://ubuntuforums.org/showthread.php?t=494158](http://ubuntuforums.org/showthread.php?t=494158)
Most importantly, here is a modified version of what you need to do (taken from that link and from my own config):

1. Install *vpnc* with Synaptic or apt-get (seems like you've done this)
2. In a terminal, run
```
gksudo gedit /etc/vpnc/default.conf
```
Your setup should look like this in the file where italics are your own stuff:
> IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec secret *password*
Xauth username *your_vpn_login_name*
Save and close.
5. ```
sudo vpnc-connect
```
6. Enter your vpn user name if prompted
Enter your VPN's password if prompted
Enter your unique login password if prompted
7. After you're done, sudo vpnc-disconnect

You can also connect using nm-applet (in your taskbar) by left clicking and using the VPN Connections submenu.

To be safe, put root only permissions on the /etc/vpnc/default.conf file (which has your password in it):
```
sudo chmod 600 /etc/vpnc/default.conf
```

Any specific information like, IPs, passwords, group names, your login name -- you will have to get from your school.

Hope this helps.

PS: Go Trojans!
:)

---

### Post by etothepi on 2008-03-11
Who are the trojans (I'm assuming you're referring to a sports team of some sort)?

---

### Post by Rocket2DMn on 2008-03-11
lol USC man, you implied that you went to or were associated with U of A.

---

