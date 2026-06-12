---
title: "VNC / SSH frustrated"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by antoniuk on 2007-03-06
I have Ubuntu 6.10 server working great with dansguardian and i have just installed and configured both ssh and vnc and can get them to work fro mthe server itself. when i try and remotely connect on the same lan via the same subnet I can not vnc or ssh into the box. I never installed or configured any firewall or set anything via IP tables. Is there something I should be doing to get access to vnc and ssh remotely that is not covered in the docs on how to get this working?

I have enabled xdmcp via login and enabled remote desktop. I was able to get a vnc connection liek I said locally and have the gnome login appear. I can not access anything remotely and it seems as if 22 and 5901 are somehow blocked

---

### Post by [S|G] on 2007-03-06
Your ISP could be blocking those ports, or you might be using a router that isn't configured to forward those ports to your computer. You could try to changing port numbers (in ssh you can do that by editing /etc/ssh/sshd_config) to see if you can connect to them. Don't forget that you'll need to tell which port you'll be connecting to with ssh (use -p portnumber)

---

### Post by antoniuk on 2007-03-06
Nope it was some firewll entries in iptables. Looks like some install or even the default server install builds some entries. Since i am behind a hardware firewall, I did not need anything blocked so i just did an iptables -F

---

