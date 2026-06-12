---
title: "port forwarding"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-12
i am having trouble forwarding my ports ( 22 & 80).
i already forwarded the ports on my westell router but i still cant 
view my server from outside the local network. can anyone give me an idea of what might be wrong. and thanks to everyone that has been helping me out with the installation of my linux box. thanks

---

### Post by apjone on 2005-11-12
just check that your forwarding them to your linux box , is your linux box using a static ip address?

---

### Post by grim918 on 2005-11-12
yes i am using a static ip address i set it up but everytime that i go and check my ip from lets say another website its still showing that i have another ip address thats different from my static ip address. someone told me that i might need to contact my ISP. I dont think that it should be that complicated though. and thanks for the help.

---

### Post by grim918 on 2005-11-12
by the way i have a network of 2 computers and i set up static ip addresses for both of them, but i only forwarded the ports on the linux box. dont know if this will help but just trying to give a visual of how i have things set up.

---

### Post by m0biu5 on 2005-11-12
If you have a router, then the websites will see that IP as your external IP..

---

### Post by dbott67 on 2005-11-12
Did your ISP assign you a static IP or are you talking about setting a static IP on your internal LAN? 

There are 2 issues at hand here:

1. Most ISPs do not generally give out static IP addresses unless you pay extra for it.  They would use DHCP to automatically assign your cable/DSL router an IP address.

Go to [this site]("http://www.stcatharines.library.on.ca/techtalk/ipaddress.shtml") using the & tell me what it reports for your IP address.
[http://www.stcatharines.library.on.ca/techtalk/ipaddress.shtml](http://www.stcatharines.library.on.ca/techtalk/ipaddress.shtml)

You can PM me the IP if you want to keep it private.

The number that you see here is your external IP address and is the number you should be trying to connect to using SSH and HTTP.

2. If you assigned static IPs to your home computers (probably something like 192.168.xxx.yyy), then your Westell router is using Network Address Translation to share a single internet connection (and single IP address) among a number of computers.  You would need to forward ports 22 & 80 to the appropriate internal IP address of your server (192.168.xxx.yyy).

-Dave

---

### Post by grim918 on 2005-11-12
how do i make my internal ip reachable from the outside of the network

---

### Post by mechanic on 2005-11-12
[QUOTE=grim918]how do i make my internal ip reachable from the outside of the network[/QUOTE]
Firstly most people don't want to make their 'internal' IP reachable from the outside of their network because it's a security risk. You, however,  seem to be running a SSH and an HTTP server inside the network that you *do* want people to reach.

Is this just on the one machine or do you have ssh servers (for instance) on all your network machines? If the latter is the case, you need more than one IP address assigned to your network by your ISP, and you need to set up the router to forward each of those IP addresses to a particular machine.

Port forwarding is what you do to overcome the security of the address translation of the router which is generally so useful for security. Incoming traffic on certain ports can then be forwarded through the router 'firewall' to the appropriate machine. Tables for arranging this are held in the router, you need to read the router docs to find out how to set this up. You could also consult any router support forum for that particular machine (e.g. on the UK ADSLGuide web site). It's not a Ubuntu problem, it's a router set up problem.

m.

---

### Post by dbott67 on 2005-11-12
As mentioned, you'll need to setup "port forwarding" in your cable router.  Check the instruction manual.  Here's a diagram of what your setup should look like.

-Dave

---

### Post by grim918 on 2005-11-12
the original intention of this thread was that i was trying to make my server accessible to the outside world. i had forwarded all the ports on my router to my linux box but it never worked. and i even changed my internal ip addresses to static. i ended up finding out that my ISP will still assign me a dynamic IP address. i did some research and found out that verizon will charge me around 80 bucks a month minimum if i want a static IP address. so i have come to the conclusion that i will not be able to set up my webserver unless i can afford the extra charge. if anyone knows of another way that i can set up a webserver please let me know. and thanks to everyone that has been helping me out.

---

### Post by dbott67 on 2005-11-12
There are a few free services, like Dynamic DNS and No-IP that will map a hostname to a dynamic IP address.  I use these services myself so that I can access my Mac, Ubuntu and XP boxes from work using VNC.

Here's my specific setup:

1.  I setup a free account at [www.no-ip.com](www.no-ip.com) and got the 'no-ip free service'.
2.  I created a hostname at one of their free domains (i.e. myname.myvnc.com)
3.  I installed their client application on my XP box that notifies the service whenever my IP changes.  I don't ever need to know my external IP address --- I just go use myname.myvnc.com, as it is mapped to my IP address.
4.  Each one of my home computers (my XP, my wife's XP, OSX and Ubuntu) each have a static IP.
5.  I setup port-forwarding in the router to forward the vnc port (5900) to my XP computer; 5901 to my wife; 5902 to OSX; 5903 to Ubuntu.  The router allows me to convert the non-standard VNC ports (5901, 5902, 5903) back to 5900 (which is the listening port on VNC server.

So, in your case, you need to do the following:

1. Verify that the services (HTTP and SSH) are running properly from within your LAN.  You'll need to access the server from another computer on the same LAN.

2. If successful, then proceed to configuring your router for port-forwarding to your server.  Check your router manual for details.

3. Register at [www.no-ip.com](www.no-ip.com) and install the client app ([Windows, OSX, Linux]("http://www.no-ip.com/downloads.php")) on your preferred computer (server or other computer on the same LAN, as the external IP will always be the same).

4. From an outside location, try to access your server at [http://your-no-ip-account.no-ip.com/](http://your-no-ip-account.no-ip.com/) (or whatever you called it).

Keep in mind that some ISPs block port 80/21/25/110 to prevent people from hosting websites/FTP/mail servers on their home networks.  Check the ISP terms of service.  You can always change your webserver to a non-standard port which shouldn't be blocked.

Also, personal firewalls (firestarter in Ubuntu) can cause issues.  Make sure you're not using any on your server that would prevent access.

Lastly, you can always put the server in the DMZ, which will forward all inbound traffic to your server.  THIS IS NOT RECOMMENDED, but is a good way to eliminate trouble spots when getting everything setup.  If successful in the DMZ, then we try to setup port-forwarding correctly.

-Dave

---

### Post by Famous Mortimer on 2008-01-12
Hmmm...this is probably the best thread to post this in - the port I was apparently automatically assigned for downloading (via Deluge) is now closed, and I'm trying to install aMule but when I check that the port is open (I even picked one at random) it was closed. How do I go about checking if the port is really open or not, then making sure the one I want stays open?

---

### Post by tannedin on 2008-02-23
i know this is a reply to a post made in Nov '05 and not sure if you have come to a solution yet, but what I do is a combination of "ddclient" and [www.dyndns.org](www.dyndns.org) ... on dyndns, you can register an account for free and a 'free domain' service.  ddclient is fairly self explanatory and will keep your ISP addy updated through the dyndns domain.  for example I have n0cturn3.homelinux.net registered to my web server for free.

You will still have to do all the steps for opening up your computer to the outside world (port forwarding and port access where applicable).

---

### Post by mangoes on 2008-03-11
> **tannedin said:**
> i know this is a reply to a post made in Nov '05 and not sure if you have come to a solution yet, but what I do is a combination of "ddclient" and [www.dyndns.org](www.dyndns.org) ... on dyndns, you can register an account for free and a 'free domain' service.  ddclient is fairly self explanatory and will keep your ISP addy updated through the dyndns domain.  for example I have n0cturn3.homelinux.net registered to my web server for free.

You will still have to do all the steps for opening up your computer to the outside world (port forwarding and port access where applicable).

I did exactly those things (register w dydns, run ddclient, forward port 22)  but can't ssh from outside into my ubuntu box. SSH within LAN is ok .  My isp does not block port 22. Any idea? 

My router is netger wgt624v2.  The closest to it in ddclient  wgt624, which I assume includes all the versions.  Wrong assumption?

Thanks

---

### Post by tannedin on 2008-03-11
to be honest after this most recent move and doing various software changes, I'm running into the same problem myself.  I'll try to post here what I do to figure it out.

---

### Post by matt79 on 2008-03-15
I have sort of the same problem but my problem is with port 80. I can use port ssh from outside of my network through port 22. How I set mine up was make the server use dhcp and set my router to allow static ip pass through to the ip address that was given to the server. So basically my server uses the ip my isp gives me. And port 22 for ssh works. The question I have is why does port 80 not. I can access my server locally from port 80 as a http. But out in the real world I can only use port 22 for ssh. Do I have to do somthing to let my server check for connections from port 80 out of my network. Or if I can access it locally does that mean that it is most likely my router?
any help would be great.

---

### Post by Wangsta on 2008-06-23
Yeah, I have a similar problem. I can SSH from anywhere, but when I forward port 80 to my Linux computer, then try to access my ip address, it just keeps loading but never gets anywhere. When  i type in my external ip address, it gets me my router's setup page. But when i enable port 80 forwarding to linux, it just keeps on loading forever.
Why isn't it working?

---

### Post by Wangsta on 2008-06-24
I haven't changed many defaults and I got this too when I forgot to use sudo:

> sadfaw2e2@server:~$ /etc/init.d/apache2 force-reload
open: Permission denied
 * Reloading web server config apache2                                          httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied


---

