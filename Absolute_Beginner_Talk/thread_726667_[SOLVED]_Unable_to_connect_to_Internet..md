---
title: "[SOLVED] Unable to connect to Internet."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by opie102 on 2008-03-16
Hey guys,

 I just tried to update my Ubuntu server 7.10 and it was unable to connect to the servers. I then tried to 

ping an outside site and got UNKNOWN Host message with any site I pinged. I can ping the router and 

can access the shared drive from any PC on the Network so i know the NIC is working correctly. 

 I checked the HOSTS file, INTERFACES file, the RESOLV.CONF file and all seem in order. If I try to restart 

the network with /etc/init.d/networking restart it gives me an SIOCSIFNETMASK: Invalid argument. Failed 

to bring up eth0.

I know I gotta be missing something here. Any ideas???


Also if you could tell me how to get a log off that box and onto the shared drive so i can post it if you 

need to see anything that would be great. That has eluded me so far.

---

### Post by opie102 on 2008-03-17
Unscrupulous bump because I cant sleep and need to ward off boredom. No better way then banging your head against a problem till the pain stops lol.

---

### Post by PapaNerd on 2008-03-17
Knowing the output from these commands would help us assist you:
```
lshw -C network
ifconfig -a
cat /etc/network/interfaces
route
ping ubuntuforums.org
ping 91.189.94.186
```

The output from any of these commands can be directed to a file on the share by doing ```
 > /(path)/(filename)
``` after the command.  The parenthesis are not part of the command, but just included to indicate that is where you insert your own values.

---

### Post by PapaNerd on 2008-03-17
Almost forgot ... it would be most beneficial to compare the same commands from another machine on the same subnet (so we can compare the subnet mask settings).  If the other machines are Windoze boxes, please do a "ipconfig /all" command.

---

### Post by opie102 on 2008-03-17
> **PapaNerd said:**
> Knowing the output from these commands would help us assist you:
```
lshw -C network
ifconfig -a
cat /etc/network/interfaces
route
ping ubuntuforums.org
ping 91.189.94.186
```

The output from any of these commands can be directed to a file on the share by doing ```
 > /(path)/(filename)
``` after the command.  The parenthesis are not part of the command, but just included to indicate that is where you insert your own values.
PapaNerd

Thank you. You actually resolved my issue with your instructions. When checking route i noticed that somehow the Gate way was set to just an *, I added the default gateway and did an update and all is well.

 Thank you.

I also learned another little trick to linux on saving output to files :)

---

### Post by PapaNerd on 2008-03-17
A missing default route is fairly common.  Glad to be the catalyst in helping you locate the problem.

---

