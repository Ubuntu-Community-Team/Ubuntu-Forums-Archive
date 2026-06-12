---
title: "a couple of questions"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-11-26
Hi,
I am trying to set up a web server. I have already installed PHP4 and Apache thorugh Synaptic. However, it seems I have to install MySQL and phpMyAdmin manually.
1. I am not sure which MySQL I have to download. I go to the site and there are tons  of different versions. Which one is suitable for use in a web server?
2. When I download, what is the usual place to save the files and/or install the softwares in? is /user/bin the place? I don't know what the convention is? For example, where should I install phpMyAdmin and MySQL?
3. How do I access CD-ROM and floppy from terminal?
4. When I assign a static (LAN) IP to my machine, I can't access Internet. When I set to DHCP it works fine. Am I missing something? For testing purposes, shouldn't I set this PC (web server) with a static IP?

Thanks.

---

### Post by joselin on 2005-11-26
1. Mysql and phpmyadmin can be downloaded throught synaptic, you don't need to download from the web.
2. See point 1.
3. Usually you have to go to /mnt/floppy or /mnt/cdrom... check your /etc/fstab... and how to mount devices (man fstab).
4. Check your router configuration. You musn't have an static ip adress for a web server.

Regards.
Jose

---

### Post by NoBullMan on 2005-11-26
Thanks Joselin. I was following the steps outlined in wiki on installing LAMP and it mentioned that MySQL and phpMyAdmin had to be downloaded and installed manually. But I found them SPM and installed. Thanks.

If I don't set the web server with an static IP address, how would I be able to access it (not knowing what the IP might be.)

TIA.

---

### Post by joselin on 2005-11-26
Check places like [DynDns]("http://www.dyndns.com/services/dns/dyndns/") who offers a free DNS service for those with dynamic IP addresses.

Regards.
Jose

---

### Post by markthecarp on 2005-11-26
Great job NoBullMan you're making progress. 

On #4, dhcp handles setting the search domains and location/address of the router/gateway. While you've got the box up with dhcp look at /etc/resolv.conf. Your dhcp client writes this file, it needs to be the same when you have the box setup with a static IP. This is the file sets the search domain, typically your isp's name and 2-3 IP addresses of your isp's DNS servers.

The gateway location/address is most likely your key problem. There is a command line way to set this but it sounds like you have Gnome running on this box so I'd suggest using System>Networking>select eth0(that may vary)>Properties in the gateway field enter the IP address of your router. Typically 192.168.0.1 or 192.168.1.1.

I've used dyndns.com for several years the only problems I've had have been my own fault.

-mark

---

### Post by NoBullMan on 2005-11-27
Thanks guys for all the help. I got the local static IP working.
I will be asking for help as I continue to set up the web server.

How can I mark a thread as "closed" or "solved", or can I?

---

### Post by joselin on 2005-11-27
> How can I mark a thread as "closed" or "solved", or can I?

You can. You must go to your User CP, then Select Subscriptions and select the thread you want to cancel the subscription. Look for the option caled selected threads, in this option you have a list where you can modify the kind of subscription for your threads.

Regards.
Jose

---

### Post by NoBullMan on 2005-11-27
You mean I have to subscribe to the thread I started in order to add it to my "subscription folder", then select it and cancel the subscription?

I was wondering if there is a way for me to mark the thread as "resolved", since I had started it, so people like you who respond to questions would know that the issue is resolved and don't waste their time.

---

### Post by joselin on 2005-11-28
You can edit your message and change the tittle appending to it something like "[SOLVED]".

Regards.

---

