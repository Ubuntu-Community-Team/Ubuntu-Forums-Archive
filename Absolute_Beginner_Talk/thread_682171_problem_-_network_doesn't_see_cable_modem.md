---
title: "problem - network doesn't see cable modem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by andy b. on 2008-01-29
greetings.  first time Linux installer here.

i have an old Pentium II system with a 266MHz CPU, 256MB RAM on an Asus motherboard.  i just installed Xubuntu from a 6.06.1-alternate-i386 ISO CD.  the installation went fine and everything seems to be okay except for network access.  i have an older Motorola Surfboard cable modem connected to a Linksys 4-port router.  i can enter the IP address to see the router and configure it and check status, and if i ping the router i get a return of 0.372ms.  when i try to ping the cable modem it comes back destination unreachable.  if i bypass the router and plug the ethernet cable directly into the cable modem i get the same destination unreachable message.  if i enter the cable modem IP address into a Firefox browser window, it returns server not found.

i know the cable modem is working because i am using it right now to post this message.  for network settings in WinXP i am using DHCP with obtain IP address and DNS server address both set to automatic.

i have never set up a Linux system before (or any Unix-based system), but i am familiar with using Unix as well as setting up Windows systems.  i am by no means a networking expert though.

any ideas or tips are appreciated.

andy b.

---

### Post by Ex-windows on 2008-01-29
Did you have the system hooked to the router/modem during install?

---

### Post by andy b. on 2008-01-29
no, i didn't have any router or modems connected during the install.  when it asked about network setup i clicked on the do it later option.  i'm guessing i need to do something to set network access up other than just plugging the modem in (although i'm not sure why i can access the router).

so, how do i set up network access?

andy b.

---

### Post by Ex-windows on 2008-01-30
It works easier when everything is hooked up during the install. But here are some links that should help at least I hope they will
NETWORK AND iNTERNET: 
Samba 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) Cool

Shareing with Windows 
[https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html) 

Gutsy 
[https://help.ubuntu.com/7.10/internet/C/index.html](https://help.ubuntu.com/7.10/internet/C/index.html) 
Great unbuntu help site
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Fiesty 
[https://help.ubuntu.com/7.04/internet/C/index.html](https://help.ubuntu.com/7.04/internet/C/index.html)  

Good luck

---

