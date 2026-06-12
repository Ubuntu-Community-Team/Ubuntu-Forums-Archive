---
title: "Konqueror can't find workgroups"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by loksipan on 2006-11-28
I have set up a Debian File Server and want to connect to it with a Hoary Hedgehog notebook.

Samba is installed on both.
smb.conf is configured as a Wins Server on the Debian machine and Wins Client on the Ubuntu machine.
i.e.
Debian:  
      workgroup = myworkgroup
      wins support = yes 
      ;    wins server = w.x.y.z

Ubuntu:
      security = user 
      wins support = no   
      wins server = 192.168.2.64


I can ping the Debian IP from the Ubuntu machine and vice versa.

Hostname settings in Debian and Ubuntu are different but Domain Name is the same - I take this to be the WORKGROUP name - I'm not sure if this is correct.

Both Debian and Ubuntu machines have fixed IPs around the router IP 192.168.2.1 ie. 192.168.2.64 and 192.168.2.25 respectively, Sub Mask is 255.255.255.0

If I use Konqueror, LOCATION->OPEN_LOCATION and enter smb:/// a blank windows opens, there is a pause of several seconds then an error report that reads "unable to find any workgroups in your local network".  ](*,) 

Any advice much appreciated.

Steve

---

