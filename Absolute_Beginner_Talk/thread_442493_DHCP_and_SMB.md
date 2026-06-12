---
title: "DHCP and SMB"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by akscooter on 2007-05-13
I'm running DHCP and Samba shares on an Edgy 64 server install. Range - 192.168.1.*

I have two problems, and I have narrowed it down to DHCP and Samba as it has to deal with pc-pc and pc-printer problems.

Problem 1
We have to xerox networked printers running TCP/IP printing. When the xerox is set to static, no one can see it, ping it, or access its web interface (from the server I can ping it). When set to DHCP, all is well, until the stupid thing goes into powersaver mode (to which I have been told you can not disable), the printer looses its IP address, and will not renew!

As a temporary work around for both printers, I have connected via USB the closest computers and shared through windows. Obviously, this can only be temporary as I don't want the computers to have to stay on all the time so someone can print.

Any suggestions on this?

Problem 2
I have a few computers that will not allow other computers to access its shares, while others can. All the computers can access the server's shares, but not other windows shares. And when set to static IP addresses, no computer can see any other computer on the network with the execption of server -pc connections.

What setting in DHCP will allow the printer renew, and is DHCP capable of telling its clients to allow communications with non-dhcp clients?

Thanks
Jon

---

