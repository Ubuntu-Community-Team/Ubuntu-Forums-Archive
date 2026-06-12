---
title: "Web server broke after DSL switch"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by bhgchris on 2007-11-14
About 5 months ago I set up a web server with Ubuntu Server. My internet connection was through cable. I recently moved and was forced to use DSL. My setup is the exact same and I am not able to access my machine from outside of the network.

Here is my setup:

```

    [Internet] -> [ DSL Modem ] -> [ D-Link 524 Router ]
                                              ||
                                              \/
             [ Roommate's Computer]----------   ----------[ Another D-Link 524 Router acting as a switch ]
                                                                                     ||
                                                                                     \/
                                                                 [Web Server]--------- ---------[Desktop 1]---------[Desktop 2]

```
I have DHCP set up on the main router to always assign 192.168.0.105 to my web server. Port 80 is also forwarded. I can access the web server just fine from my local network using the IP or the hostname. I was ( and still am ) a complete noob when I set all of this up.

To be honest, I'm not sure if it is only a web server issue because I can't access any of my machines from the outside. I tested a Ventrillo server on a Windows computer and it only gave me local IPs for access.

My IP is dynamic and I will be using DynDNS.com once I figure out how to access my network from outside.

Any help would be greatly appreciated


Chris

---

### Post by Zeosa on 2007-11-14
It's more than likely that your DSL provider is filtering incomming tcp connections on port 80. Most ISPs now have have TOS restrictions against running servers on their networks.

Try running nmap against your ip from outside of your network and see if port 80 shows a status of 'filtered'.

One way around this is to use SSL which runs on tcp/443 and access the site via https:// .....you'll have to set up apache with ssl support, but I've found that providers rarely block 443. The other alternative is to forward a different port such as 8080, but users connecting to your site will have to know which port to use which can be a PITA.

---

### Post by bhgchris on 2007-11-14
Thanks for the reply, Zeosa.

I don't believe this is the problem. I read my ISP's TOS. I will call them to double check. 

It's not just port 80. I also have a squid proxy server installed and ssh. I can't access through port 22. Also, as I mentioned above, I can't even use a Ventrillo server on one of my Windows desktops.

---

### Post by bhgchris on 2007-11-17
I figured it out. I had forgotten my webserver was using a static IP. I set it back to get the IP with DHCP. I use DHCP on my router so I don't need it on my server. 

Thanks for your help though.

Chris

---

