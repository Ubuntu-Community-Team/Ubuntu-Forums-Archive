---
title: "Static IP problems."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by bagbiter on 2007-05-11
I am connected to internet through a wireless router. It has a dhcp function enabled that gives ips 192.168.1.xxx.

In Windows I could still set 192.168.1.108 as my IP and it would become my IP in the router. However if I set my  ip to 192.168.1.108 in Ubuntu, both ifconfig and the network settings-gui tells me my IP is 192.168.1.108, but my router tells me that it's 192.168.1.103..! also i have opened correct ports (for torrents, WoW, etc) in the router and in Firestarter, but the applications still says that the ports are closed.

is there anywhere i can see  my REAL, actual IP?

---

### Post by BHelts on 2007-05-11
Not too sure about the port forwarding, although if the router thinks you are .103 and you are really .108 then that would surely cause a problem.  As a 'best practice' you should probably set your static IP outside the router's DHCP range, or turn DHCP off.  Also, are you certain that the .103 address is your computer?

---

### Post by bagbiter on 2007-05-11
weird.. i have set my ip outside the dhcp range, and changed the port forwarding to my new ip. but now my computer doesnt show up in the list of connected clients in the router..and the ports still dont seem to be opened

---

