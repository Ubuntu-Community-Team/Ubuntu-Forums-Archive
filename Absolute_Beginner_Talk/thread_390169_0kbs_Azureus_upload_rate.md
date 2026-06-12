---
title: "0kb/s Azureus upload rate"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by HeyItsMatt on 2007-03-21
Hey everyone, I have been having a horrible time trying to get Azureus to work on Ubuntu.  I can get a list of seeds and peers, and I get a small download rate going, but my upload rate is always 0kb/s.  

I am using a dual-boot system with Ubuntu and Windows on different partitions.  I am behind a DI-624 D-Link router (UPnP enabled), and I am using a firewall (Firestarter).  I have tried setting up a Firestarter Policy to allow BitTorrent service (also tried unknown service) on the same port listed in Azureus's Tools / Options / Connection window, and I have tried turning off Firestarter entirely - neither of these worked.  I have tried multiple ports (a default port selected when Azureus was installed, a generic BitTorrent 6881-6889 port, and a 49152–65534 range port suggested in the Azureus wiki).

When I put my computer into my router's DMZ, I started to be able to upload the file.  The NAT reachability test in Azureus also returns 'OK', which it never does otherwise.   However, when I use Azureus in Windows, I don't have to do this - the file uploads and downloads at a decent rate without the computer being in the DMZ.  

I've been trying to understand all this stuff, but I am a Linux newbie and (unfortunately) not a computer expert, so it's just a little too overwhelming.  I'd kind of like to avoid having to do some kind of port forwarding with my router, because A) I'd have to figure out how to switch to a static IP instead of DHCP, and B) I barely understand what I'm talking about as it is, and C) I dunno why I'd have to do that if I don't need to on Windows.  

What am I missing here guys?  I've seen a couple other Azureus-related threads in the forums but they were unable to help me. I apologize if I am asking a question that's already been answered.

Thanks for reading!

---

### Post by dgg222 on 2007-03-21
I'm not too sure but I think ubuntu blocks ports by default. Try entering these into the terminal then run azureus.

sudo iptables -I INPUT -p tcp --dport <port number> -j ACCEPT
sudo iptables -I INPUT -p udp --dport <port number> -j ACCEPT

---

### Post by nudnik on 2007-03-21
> **HeyItsMatt said:**
> Hey everyone, I have been having a horrible time trying to get Azureus to work on Ubuntu.  I can get a list of seeds and peers, and I get a small download rate going, but my upload rate is always 0kb/s.  

I am using a dual-boot system with Ubuntu and Windows on different partitions.  I am behind a DI-624 D-Link router (UPnP enabled), and I am using a firewall (Firestarter).  I have tried setting up a Firestarter Policy to allow BitTorrent service (also tried unknown service) on the same port listed in Azureus's Tools / Options / Connection window, and I have tried turning off Firestarter entirely - neither of these worked.  I have tried multiple ports (a default port selected when Azureus was installed, a generic BitTorrent 6881-6889 port, and a 49152&#8211;65534 range port suggested in the Azureus wiki).

When I put my computer into my router's DMZ, I started to be able to upload the file.  The NAT reachability test in Azureus also returns 'OK', which it never does otherwise.   However, when I use Azureus in Windows, I don't have to do this - the file uploads and downloads at a decent rate without the computer being in the DMZ.  

I've been trying to understand all this stuff, but I am a Linux newbie and (unfortunately) not a computer expert, so it's just a little too overwhelming.  I'd kind of like to avoid having to do some kind of port forwarding with my router, because A) I'd have to figure out how to switch to a static IP instead of DHCP, and B) I barely understand what I'm talking about as it is, and C) I dunno why I'd have to do that if I don't need to on Windows.  

What am I missing here guys?  I've seen a couple other Azureus-related threads in the forums but they were unable to help me. I apologize if I am asking a question that's already been answered.

Thanks for reading!

Very few people have been able to get Azureus to function properly with Ubuntu. Although it is a fine Windows client, the Linux version is just too problematic. 

If you download one file at a time, use BIttornado. If you want an Azureus-like client (but one that might actually work, depending on your system) give Deluge a try. Its available from GetDeb at [www.getdeb.net](www.getdeb.net). A word of caution; Deluge doesnt seem to work well with old, low power CPUs.

---

### Post by scxtt on 2007-03-21
do sudo iptables -L if you think ubuntu "blocks" ports by default - which i don't think is the case ... it doesn't have any "listening services" by default, but it shouldn't be blocking ports ...

are you forwarding the port range 6881-6889 to your ubuntu IP?

DMZ sends ALL traffic to that IP, so it's basically a catch-all - not a real solution ...

you'll need to both forward that port range and allow firestarted to let the traffic through ...

---

### Post by HeyItsMatt on 2007-03-22
Hey guys, thanks for the responses!

dgg222: Yeah, I actually saw that in the Azureus wiki, but I guess I am kind of wary about messing with IPtables from the command line when I don't know what I'm doing or don't even know what the commands mean - also, I thought that Firestarter was basically just a GUI to modify IPtables?

Despite that though, I think I got a little closer to the problem - I noticed that on Windows, my router was automatically getting a couple of rules added to its "firewall" section related to Azureus UPnP when I started Azureus.  It looked like Azureus's UPnP plugin was automatically configuring the router in Windows, and on Linux it is not doing that - I have an error message about "failing to initialize" in the UPnP log section of Azureus when I check it. 

I've tried a couple other BitTorrent clients though, like KTorrent, and they seem to be working... it's strange though, I thought I disabled UPnP earlier on Azureus and it still wouldn't work right, even though these other clients are working fine without UPnP or router configuration or anything.  *Shrug*  I think I will just use an alternate client instead of Azureus, rather than having to get a static IP and make more router rules.

Also, thanks for the Deluge suggestion, nudnik.  I'll check it out.

---

### Post by Josh1 on 2007-03-22
> **nudnik said:**
> Very few people have been able to get Azureus to function properly with Ubuntu. Although it is a fine Windows client, the Linux version is just too problematic. 

If you download one file at a time, use BIttornado. If you want an Azureus-like client (but one that might actually work, depending on your system) give Deluge a try. Its available from GetDeb at [www.getdeb.net](www.getdeb.net). A word of caution; Deluge doesnt seem to work well with old, low power CPUs.

Wait... what? I've been using azereus and Ubuntu for ages and ages and I haven't had one problem. I used firestarter to allow the ports and did port forwarded since my server needed dmz.

---

