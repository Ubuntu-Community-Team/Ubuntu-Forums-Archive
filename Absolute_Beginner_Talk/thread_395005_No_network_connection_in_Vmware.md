---
title: "No network connection in Vmware?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Sprogg2001 on 2007-03-27
Hello all 

Im very new to linux unbuntu in general just wanted to check out the new distro im on 6.10 downloaded the .386 distro and launched it in vmware using the standard virtual machine settings  and selecting ubuntu as the distro type, installation worked fine ( I didnt think to check the net connection using the live cd) I just went ahead with the install since it worked on ubuntu 6.06 I thought it would work on 6.10  but I cannot get a connection to the internet, I used the bridged networking mode and that didnt work I used Nat mode in vmware virtual machine settings and that didnt work either I tried using the network tools to ping my router 192.168.2.1 for some reason on my windows machine my DNS address is 4.2.2.2 (dont know why) so I changed it to that in ubuntu on vmware and nothing.

any advise on where to go from here would be great

---

### Post by oilchangeguy on 2007-03-27
i've had ubuntu 6.06 installed on vm ware workstation 5.0 and NAT worked great. not sure about 6.10 issues, you might want to go back to version 6.06, since it did also work for you.

---

### Post by Sprogg2001 on 2007-03-27
I know I mean how simple do you want it to get all the virtual hardware works, its a direct ethernet connection so no usb drivers its should just work??? 

I even switched off the firewall on the xp machine vm is running on I dont understand it

---

### Post by Sprogg2001 on 2007-03-27
:lolflag:  How stupid can you get, Net Connection was down it just came back up just before I started posting LOL talk about simple!

---

### Post by jdruin on 2007-11-21
In my case, I had to completely shutdown ZoneAlarm on my XP box and go to my router and explicitly grant access to the MAC address displayed in the ubuntu terminal when typing ifconfig.

---

