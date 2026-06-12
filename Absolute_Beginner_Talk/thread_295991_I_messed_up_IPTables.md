---
title: "I messed up IPTables"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-11-08
I guess my recent newbie successes made me cocky, and I meddled in something I didn't understand.  Now I'm paying for it.  I installed Firestarter from the Synaptic Package Manager, and configured it, safely, I thought.  Turns out I was wrong.  Now I cannot access the Internet.

I can ping all other devices on my LAN, but I can't access the WAN.  

My "Inbound traffic policy" allows nine devices on the LAN to send inbound traffic to my Linux machine.  All IPs are in the 192.168.0.xx range.

Allowed inbound services are SAMBA, SSH, and FTP.

I have a permissive "Outbound traffic policy."  No connections are denied.

Now, when Firestarter is started or disabled, I cannot get on the internet.  

I am way over my head on this, but I suspect that the IPTables contain some configuration info that Firestarter does not show.  I have not been able to figure out where to look at the IPTables directly -- or even if it is possible.

Any help will be appreciated.

---

### Post by David_T on 2006-11-08
If you want to see what's in iptables, do:
sudo iptables --list
If you want to remove everything in iptables, do:
sudo iptables --flush

---

### Post by DaveBorealis on 2006-11-09
> **OldDogNewTricks said:**
> 
Now, when Firestarter is started or disabled, I cannot get on the internet.  


By disabling Firestarter you mean you clicked the stop button?  If so, then you should have no firewall between you and the WAN.  

As a shot in the dark, can you ping google?
```
ping -c1 google.com
```

If the above doesn't work, then try using one of google's IP addresses.
```
ping -c1 64.233.167.99
```
If the first ping doesn't work, but the second one does, then it's a problem with DNS. 
Dave

---

### Post by OldDogNewTricks on 2006-11-09
> **DaveBorealis said:**
> By disabling Firestarter you mean you clicked the stop button?  If so, then you should have no firewall between you and the WAN.  

As a shot in the dark, can you ping google?
```
ping -c1 google.com
```

If the above doesn't work, then try using one of google's IP addresses.
```
ping -c1 64.233.167.99
```
If the first ping doesn't work, but the second one does, then it's a problem with DNS. 
Dave

Dave,

I gave both pings a try, and the first fails but the second succeeds.  So it looks like my problem may not be IPTables at all. (I stopped Firestarter, and flushed the IPTables, and still cannot connect.)

But I don't have a clue as to how to repair DNS -- or what I did
to damage it.

Marvin

---

### Post by handy on 2006-11-09
[This is a great how-to for ip-tables]("http://doc.gwos.org/index.php/IptablesFirewall")

---

### Post by aidanr on 2006-11-09
try going into 
***system->administration->networking***
hit the ***dns*** tab and see if there are any dns servers listed
if not then add the ip of your router
you may have to 
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
i'm not sure if thats necessary or not
replace eth0 with your connection

---

### Post by DaveBorealis on 2006-11-09
> **OldDogNewTricks said:**
> 
But I don't have a clue as to how to repair DNS 


Follow aidanr's advice and you should be set to go.  If you don't know what your DNS IP addresses are, you can probably get them from you ISP.  That information gets stored in '/etc/resolv.conf'.  If you already have addresses in that file, then perhaps your ISP changed DNS and you need to get the new ones.

Dave

---

### Post by handy on 2006-11-09
If you are using a router, you can access it through your web browser & see what your ISP's DNS addresses are too.

You may need to look at the documentation that came with your router to find the IP, user name & password to access it.

Here is a link to the [OpenDNS quick walk through]("http://www.opendns.com/start/") for changing your router's DNS, it should be able to deal with your router.

---

