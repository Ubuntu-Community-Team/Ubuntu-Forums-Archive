---
title: "[SOLVED] Edubuntu 7.10 wireless network not persistent"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by impalerau on 2007-10-23
Hi,

this is my first foray into linux and my frst forum post.  Please be gentle :)

I have successfuly installed edubuntu 7.10 on my daughter's machine and connected to my wireless network using the ndiswrapper with the help of the instuctions for 7.04 at [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

Every time I reboot I lose the wireless conection and have to repreat the "sudo depmod -a" and "sudo modprobe ndiswrapper" commands to enable wireless networking again. Then I have to use the "Connect to Other Wireless Network.." to re-enter the network name and WEP details.  At least that is working consistently.

Can the set up be made persistent or is this something I have to live with?

In case it matters, I'm using  a Netgear WG311 v3 PCI card.

Thanks in advance,
Vlad.

---

### Post by n3tfury on 2007-10-23
in 7.10 there should be a network monitor icon.  click on that and your network (or any available) should show up.  click on the network and it should start pulling dhcp (if you have your router setup that way)

---

### Post by impalerau on 2007-10-23
Yes, the network icon is there but the only 2 entries in the drop down after a reboot are 'Wired network" and "Manually configure" (or words to that effect).  I'm at work now so don't have the box in front of me to read the exact menu text.  The other (wireless) entries do not appear untill I have rerun the previously mentioned commands.

Then I have to select "Connect to another network" and re-enter the network name and WEP details again to reconnect.  Once I have done that, it connects immediately, getting an IP addres from the DHCP etc.

---

### Post by impalerau on 2007-10-24
Please ignore this thread, I've reposted i the Networking & Wireless forum.

---

### Post by impalerau on 2007-10-30
Please see resolution in networking forum:- [http://ubuntuforums.org/showthread.php?t=589365](http://ubuntuforums.org/showthread.php?t=589365)

---

