---
title: "Problems with ddclient"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by splendid on 2007-03-13
Trying to access my machine using Dyn Dns.  I had ddclient  and everything all setup and working, but am unable to access using my Dyn Dns URL.  I verified that ddclient is up and running.  I can access it by IP, but not by the URL .  Any ideas on what to check, or if something could have changed when I moved?

Thanks,

Splendid

---

### Post by raidlost on 2007-03-13
have you done

#nslookup (URL)

??

---

### Post by splendid on 2007-03-13
No, I have not tried that.  Do you just enter the command from root in a terminal window?

---

### Post by raidlost on 2007-03-13
yup

at root prompt

use mouse to copy output to this thread lets see

---

### Post by splendid on 2007-03-13
I got a Non-Authoritative Answer and it listed the URL and the IP address.

---

### Post by splendid on 2007-03-13
> basement.homelinux.net
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   basement.homelinux.net
Address: 69.139.125.145

---

### Post by raidlost on 2007-03-13
if 69.139.125.145 is your public interface ip and is correct 

are you using a router?
is it forwarding outside requests for the IP to the correct internal machine?
if so you might need to allow forwarding for the URL to the correct internal machine.

Simply ((((

I suspect you have NAT enabled but not port forwarding, if you are using a router.

))))

do 

#tracepath 69.139.125.145

see if the packets leave the lan

---

### Post by splendid on 2007-03-13
Thanks.  I did the tracepath and I am getting no reply.

---

### Post by raidlost on 2007-03-13
check if port forwarding is set to receive 69.139.125.145 and forward to lan ip for the local machine on the router

---

### Post by splendid on 2007-03-13
Since my ip address changes every now and then, would this have to be updated.  It is strange, I have not changed anything on my settings at all on the router and it worked before.  The only thing that changed was my Dyn Dns account was closed, and I had to open it back up.  However, I confirmed that my ddclient daemon is running and everything is up to date.

---

### Post by splendid on 2007-03-13
Okay more info.  Just got this from my router.  Looks like it is denying the connection requests for some reason.


Mar/13/2007 10:24:52 	Drop TCP packet from WAN	213.245.203.8:62596	69.139.125.145:62669	Rule: Default deny
Mar/13/2007 10:24:49 	Drop TCP packet from WAN	213.245.203.8:62593	69.139.125.145:62669	Rule:

---

### Post by splendid on 2007-03-13
Raidlost, Thanks for all your help!!!  I got it working now.  What happened was I connected to the network through my router with my laptop first.  Therefore, the laptop was assigned the first local ip address 192.168.0.100, instead of my server that was booted up second.  All the rules on my router are setup with the server as 192.168.0.100, not 101.

I appreciate all your help.  There is no beating the Ubuntu community!!!

Splendid

---

### Post by raidlost on 2007-03-13
:popcorn: 

Glad I could point you in the right direction

---

