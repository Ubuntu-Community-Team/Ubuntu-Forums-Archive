---
title: "How to network 2 Linux boxes on DHCP?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-08-05
The Community Forum Documentation says: "Browse Network Computers
To view computers on the network, open Places &#8594; Network Servers. 

You may need to enter a username, password, and domain. You should obtain these from your network administrator."
___

QUESTIONS:  

In Ubuntu 7.04, under PLACES -> Connect to Server, it asks, Service Type? Server Name?  Port?  Folder? and Name to use for connection?

I am on computer L.  The partition is called RLH-linux.  
I want to connect to computer Z, and the partition called BGH-linux.

The PCs are connected to the Internet through a cable modem and DHCP router, both working fine.  The IP addresses of each change often (with cable service irregularities).  Static IP addresses are not an option here.

How can I get them to see each other and share files?

---

### Post by xpod on 2007-08-05
You can use remote desktop if your all set up correctly or you could install the openssh server on one one the machine or both if you want to access them both both ways..

EDIT you need to install nfs for best method of sharing i think
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

---

### Post by bogolisk on 2007-08-05
> **bettyhills said:**
> The Community Forum Documentation says: "Browse Network Computers
To view computers on the network, open Places &#8594; Network Servers. 

You may need to enter a username, password, and domain. You should obtain these from your network administrator."
___

QUESTIONS:  

In Ubuntu 7.04, under PLACES -> Connect to Server, it asks, Service Type? Server Name?  Port?  Folder? and Name to use for connection?

I am on computer L.  The partition is called RLH-linux.  
I want to connect to computer Z, and the partition called BGH-linux.

The PCs are connected to the Internet through a cable modem and DHCP router, both working fine.  The IP addresses of each change often (with cable service irregularities).  Static IP addresses are not an option here.

How can I get them to see each other and share files?


I think we're not clear yet on your setup: do you have a router? the dhcp server is your ISP or your router? I.e. does your ISP assigned IP to your computer or was it owner router?

---

### Post by xpod on 2007-08-05
> 
I think we're not clear yet on your setup: do you have a router? the dhcp server is your ISP or your router? I.e. does your ISP assigned IP to your computer or was it owner router?

I jumped to conclusions myself there :)

I just use an Ubuntu box as a router/firewall with separate nic`s for ics and sharing to other pc`s and it`s been pretty starightforward thankfully.:)
We do have a second completely separate net connection and the DHCP addresses from our isp on both rarely change even though we turn everything off most nights,even communication between the 2 mini networks gets away with the DHCP addresses....most of the time

I`ve not had to change any hosts files or firewall settings for a fair old time:)

Still....

---

### Post by bettyhills on 2007-08-05
The building is connected to the Internet through a cable modem.  The cable modem connects to a router.  8 PCs in the building connect to the Internet through the router and modem.  All are working fine. All surf the web, enjoy email, etc.  

I found many tutorials on how to network Linux PCs to each other if the IP address is static.  We require **DHCP** (dynamic IP).  Because the IP addresses of each PC change often, static IP addresses are not an option here.  Comcast reassigns our address many times a week, and when we reset the system, the PCs IP addresses change.  It is impractical to give them static IP addresses, as reconfiguring would become a full time job.

Two of PCs are dual boot XPLinux boxes.  Each sees the six Windows boxes on our internal LAN, AND can see the Windows partition on the other Linux box.  Neither Linux box can see the other Linux box EXT3 partition.

How can I network them so that they SEE EACH OTHER, and share files on the other's Linux partition?

---

### Post by dfreer on 2007-08-05
Well, normally, an ISP only provides 1 IP addess, dynamic or static, and you use the NAT function on your router in order to have multiple computers share that one IP address. The router, in that case, is in charge of handing out private IP addresses via DHCP, and not the ISP. Although you may very well have an ISP that gives out multiple addresses, and the router may be acting simply as an firewall. What you need to do to check this would be to examine the computer's IP address, and compare it to the external IP address. This site will give you your current external IP:
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)
If they do not match, then you are most likely dealing with the router's DHCP function and not the ISP giving out dynamic IP addresses. 

You can use dyndns.com or no-ip.com to map a dynamic hostname to a specified IP address. Normally, the client will use the external IP address (this enables you to access the machine from the internet at large), but you can specify it to use the local LAN IP address instead. This would allow you to access the LAN machine by using it's FQDN, like myhost.dyndns.org.

Another option is using Samba, or BIND to create a local nameserver. This solution is similiar to the way you can browse LAN's in Windows and see computer names, instead of IP addresses. You can connect to the other computer using hostnames instead of IP addresses (say *mymachinerocks* instead of 192.168.2.23), which means it doesn't matter whether you are using DHCP or static. AFAIK, you cannot use hostnames of linux machines unless you do something like this.

In reality, all servers (and file sharing is generally considered a network service) should have static IP addresses. SSH, Samba, and NFS can be used to share files, with SSH probably being the eaisest to set up. Samba would allow you to share files with both linux and windows machines.

EDIT: also, linux does not usually share partitions, they share folders.

---

### Post by bettyhills on 2007-08-05
Thanks for the rapid and helpful reply.  

So, it sounds like Samba is the best bet if I want both Linux boxes to see each other (share with each other) AND see and share with the Win boxes?

Can I use Samba without using dyndns.com or no-ip.com to map a dynamic hostname?  Can I use it with dynamic IPs?

When Comcast cuts us off and reassigns an external ip address as it reconnects service, we must take all the PCs down and reset the modem and router.  The router reassigns IP addresses to the PCs randomly.  Static IPs are not practical.

A peripheral question:  Each Linux box was assigned a machine-name when Ubuntu was installed.  It shows up in Terminal.  Is that good enough, or must I rename each one in Samba?

---

### Post by dfreer on 2007-08-05
If you do not want to try static, that's more than fine and we'll try helping you out. But I think it is worth reconsidering, it'll make things a bit eaiser. 

First, as for reseting your router: You should be able to still make use of an Static IP address, with or without the router's help. Consider my network, as an example. I have a private network of 192.168.2.XXX, with a subnet mask of 255.255.255.0, and the router is located at 192.168.2.1. I can specify any machine on my network to use a static IP (not in the router config, but manually on the machine itself), such as 192.168.2.5, and as long as I specify the gateway and DNS server as being 192.168.2.1, I can access the internet exactly the same was as if I were using DHCP. Furthermore, any network machine on the same subnet is able to access my files at 192.168.2.5. 
Generally, you should specify the machine as being static in /etc/network/interfaces file, and on the router as well if possible. As long as you don't reset the router to it's default configuration, it should keep the information about that static IP and continue using it, although things will work even if it resets everything.

Samba is one of the best methods for sharing files in a mixed OS enviroment, although SSH works great for Linux <-> Linux. Once you get Samba up and running, you should be able to access the linux machine from windows either using: 
Start > Run > //*your_linux_hostname_here*/
Or by browsing the network, although I find the above method to resolve MUCH quicker.

You can run Samba normally, without using dyndns.com. That solution is generally used for running a home web/SSH/etc server, so that anyone in the world can access it. The reason I brought it up is because it can be used on a LAN, it's just another solution to try if nothing else is acceptable.

The default hostname in Samba is the machine's hostname, although you can tell Samba to use a different name (if you feel like not sharing the machine's hostname).

The ubuntuguide.org link below has some fairly simple how-to's on basic filesharing, if you don't know how to setup samba. Hope this all helps!

---

