---
title: "Hosed my internet connection"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-21
I hosed my internet connection. 

I added, on the DNS tab of the network applet, 208.67.222.222 and  208.67.220.220 which I got from this post [http://ubuntuforums.org/showthread.php?t=416447&highlight=nameserver](http://ubuntuforums.org/showthread.php?t=416447&highlight=nameserver) 

Once I did this I lost all interent connection . I  removed these two leaving the two I had before, but I still can't connect. I checked Firestarter and all outgoing traffic is permitted. I rebooted, although I didn't think that was needed, but no luck.

I'm in Windows now and used an applet (ID Serve, from Gibson Research, the ShieldsUp guy) and the IP addressed resolved to opendns.com. 

Obviously if I can't resolve this, I'll have to go back to windows, something I don't want to do. 
How can I fix this?

---

### Post by Patrick K on 2007-04-21
I have determined it is defiantly a DNS problem. I got on this site using the IP address 82.211.81.186. Entering a domain name returns the Firefox error "Server not found."

---

### Post by Austin_KW on 2007-04-21
Can you ping 208.67.222.222

Also try a manual lookup from the command line "dig @208.67.222.222  google.com"

Sometimes ipv6 and dns dont mix very well. Have you disabled ipv6 or ipv6 dns in firefox. 

To disable ipv6 edit /etc/modprobe.d/aliases and change the line "alias net-pf-10 ipv6" to "alias net-pf-10 off #ipv6" . You will need a reboot.

To just disable ipv6 DNS in firefox type "about:config" enter "ipv6" into the filter and double click on the entry to change it to true.

---

### Post by Patrick K on 2007-04-22
I'm on Windows right now but will try your suggestions when I reboot. ipv6 is turned off in Firefox. I'm not sure about any where else. Pings are working but I'll try  what you suggested. Thanks.

---

### Post by Patrick K on 2007-04-22
Back in Festy. 

Yes, I can ping 208.67.222.222

I got a response from Google query I don't know what that tells me, though. I did a dig on my ISP's name server and got a response from it. 

ipv6 is off in the aliases file. 

Is there any place else the DNS data might be stored?

---

### Post by Patrick K on 2007-04-22
I don't know how but the hosts file got scrambled. I had a backup and reinstated it. Looks like I'm back on line. Thanks for your help Austin.

---

