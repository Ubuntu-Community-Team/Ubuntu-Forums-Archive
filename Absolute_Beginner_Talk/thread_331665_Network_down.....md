---
title: "Network down...."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by zdotz on 2007-01-04
Brand new to Linux just installed Edgy 2 days ago. Every time I reboot the computer the resolv.conf file gets overwritten to:
 
nameserver 192.168.0.1
 
(Why i'm not sure but I saw that others were having this issue so I figured I would tackle it at a later date.) This is my routers address but this router does not work well as a nameserver. For the last couple of days I have just been editing it (resolv.conf) to read:

nameserver 208.67.222.222
nameserver 208.67.220.220

(OpenDNS servers) 
   Today I rebooted, logged in, started up firefox, saw that it was woefully slow and remebered I needed to change the resolv.conf. Shut down firefox, sudo gedit /etc/resolv.conf used the OpenDNS settings and saved the changes. Fired up Firefox and nothing. Ping gateway, nothing. Ping other computers on that segment, nothing. Ping self, reply(s). Ping loopback, reply(s). I typically have my adapter set staticly at 192.168.0.3;255.255.255.0;192.168.0.1 so I tried to aquire dynamicly and nothing. I have another network adapter that is installed in this computer so I tried that with the above static settings as well as dynamic and nothing! There are other computers that share this network and they are not experiencing any problems. 

   I'm not sure how to troubleshoot this problem any further you're help will be greatly appreciated. I'm sure I havent provided you all with enough information so ask away.

TIA

---

### Post by zdotz on 2007-01-04
Problem solved. 

I am so dumb. I had the ethernet cable always plugged into the adapter that was disabled. Oh my goodness......time for bed.

---

