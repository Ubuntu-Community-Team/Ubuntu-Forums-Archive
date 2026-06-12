---
title: "Web Server on my computer?"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by shutupchuck on 2005-08-22
I'm trying to run a website off of my computer and I downloaded and installed Apache 2.0 and it said that it was installed properly and when I type localhost into my web browser it comes up with my index.html page but I cannot access it from another computer. I think the server is already running because when I go into the bin  directory of the Apache2 folder and run **apachectl start** it says 
[I](98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs[/I]

Please help, I know this is pretty simple but thats why I'm posting in the newbie section.
Thanks
-Chuck

---

### Post by KingBahamut on 2005-08-22
check ports.conf in /etc/apache2

---

### Post by shutupchuck on 2005-08-22
It says** Listen 80**

---

### Post by Ride Jib on 2005-08-22
Since you are able to see it from your local machine, that means it is not an apache problem. Are you behind a router? If so, port forward 80 to your machine.  Do you have port 80 firewalled? If so, you will need to unblock it. 

Also, it is entirely possible that your ISP has blocked certain ports. You can try changing apache to run on something like, port 8080 and see if that can be viewed outside your computer.

---

### Post by shutupchuck on 2005-08-22
Ok I have a couple questions:

I changed the port in pots.conf to 8080 but I don't know how to stop and restart the server daemon. 

I am using a router but I don't know if I have a firewall. I just installed ubuntu so everything should be default. 

I appreciate all your help a lot, thanks. 
-Chuck

---

### Post by xequence on 2005-08-22
I dont know about this but one thing... Many ISPs dont allow you to run a server. Check on their website to make sure ;)

---

### Post by Ride Jib on 2005-08-22
[QUOTE=shutupchuck]Ok I have a couple questions:

I changed the port in pots.conf to 8080 but I don't know how to stop and restart the server daemon. 

I am using a router but I don't know if I have a firewall. I just installed ubuntu so everything should be default. 

I appreciate all your help a lot, thanks. 
-Chuck[/QUOTE]

to restart the service: sudo apachectl restart

log into your router and make sure your port forwarding is turned on to redirect web requests (port 80, or 8080..l whichever you specify) to  your specific machine.

---

