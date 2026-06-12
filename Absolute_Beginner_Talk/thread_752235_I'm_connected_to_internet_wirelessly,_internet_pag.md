---
title: "I'm connected to internet wirelessly, internet pages won't load though"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by digimas on 2008-04-11
I also have a d-link wireless router and I'm connected through a wireless usb adapter. It says that I'm connected and shows bars at the bottom right side of my screen, however when I try loading sites like yahoo.com or msn.com it won't work. However I can get to google.com just fine for some weird reason. When I try getting to a site such as yahoo.com I can see stuff happening in the bottom left side of the browser such as connecting to yahoo.com or retrieving data from yahoo.com but it takes a long time and after awhile it just says done but the screen is blank white. Has anyone found a solution to this because I don't know what to do. I've tried other things like changing code in some files but to no avail. Any help would be greatly appreciated.

---

### Post by Het Irv on 2008-04-11
Have you tried resetting your wireless router or your modem?
You might be having a problem with DNS.

---

### Post by aeiah on 2008-04-11
it could also be an ipv6 issue. try searching for a way to disable it (im at work and havent time to search). its probably a DNS issue though. you could try openDNS if your ISPs DNS servers are crap (i know mine are, but my speeds twice as fast as any other so im not too bothered)

---

### Post by Het Irv on 2008-04-11
The IPv6 settings are in about:config (open a new tab, and type about:config)
Search for network.dns.disableIPv6 and change it to true.

---

### Post by digimas on 2008-04-11
The IPv6 settings are in about:config (open a new tab, and type about:config)
Search for network.dns.disableIPv6 and change it to true.

I already tried the whole changing IPv6 to true but nothing different. I also changed some of the coding that had to do with IPv6 but that didn't change anything as well. Could you describe what I need to do to fix a DNS problem. I'm not sure what DNS is but it might be the solution.

---

### Post by Het Irv on 2008-04-11
DNS (domain name sevice), changes domain names into ip addresses.  Either your wireless router will do this or, in most cases, your modem (Cable, DSL, or whatever you have).  Resetting these can sometimes take care of your problem.  The best way I have found to do this is to unplug your modem and your router, and turn off your computer.  Then turn back on the modem, wait for it to come up, turn on the router, wait, and then turn on your computer.

Tell me if that doesn't work, I will try to help you more.

---

### Post by Weidbrewer on 2008-04-11
> **Het Irv said:**
> Have you tried resetting your wireless router or your modem?
You might be having a problem with DNS.

That was what I was going to come in here to suggest.  The connection between my laptop and my Verizon wireless router often appears to be connected, when there are really errors going on.  Turning the router off for 30 seconds and then letting it reboot generally solves this problem.

---

### Post by digimas on 2008-04-11
> **Het Irv said:**
> DNS (domain name sevice), changes domain names into ip addresses.  Either your wireless router will do this or, in most cases, your modem (Cable, DSL, or whatever you have).  Resetting these can sometimes take care of your problem.  The best way I have found to do this is to unplug your modem and your router, and turn off your computer.  Then turn back on the modem, wait for it to come up, turn on the router, wait, and then turn on your computer.

Tell me if that doesn't work, I will try to help you more.

I just did what you suggested in the exact order but I'm still getting the same result. It won't load pages yet it says I'm connected to the internet. The weird thing though is that I can get the google homepage to load without a problem and sometimes when I enter a search term in the google search bar it will come up with results but this happens rarely. When I click on any of the links from the search results it never comes up with the webpages however. When I set up my internet connection I didn't do anything. It automatically detected my wireless connection and connected me. Were there some numbers that I was supposed to punch in somewhere? I really want this to work but its frustrating.

---

### Post by Whiffle on 2008-04-11
Try pasting this into your browser address bar, its the ip for yahoo:

209.131.36.158

If it loads, then its a dns issue i should think.  Also, could you post the contents of /etc/resolv.conf

---

### Post by pseudo-random on 2008-04-11
How far away are you from this router and how many other networks are in your area?

---

### Post by digimas on 2008-04-12
> **Whiffle said:**
> Try pasting this into your browser address bar, its the ip for yahoo:

209.131.36.158

If it loads, then its a dns issue i should think.  Also, could you post the contents of /etc/resolv.conf

Did this and it finally loaded!!! How can I solve this dns issue? 

Here's contents of /etc/resolv.conf :

nameserver 192.168.0.1

---

### Post by digimas on 2008-04-12
Could anyone offer more help, I think I'm on the right path with this. As I said earlier it did work when I typed in the Yahoo ip address. Everything loaded just fine but when I type in yahoo.com into the search it doesn't load. Same with most pages except for google.com

---

### Post by Whiffle on 2008-04-12
Hmmm, yeah its dns alrite.  I really don't know what to say since I have similar issues on my network at home, but only over the wireless.  Wired works fine.

Do you know the ip of your router?  Is it the same IP as is listed in resolv.conf (192.168.0.1)?  If nothing else you could paste in the dns servers for opendns for temp fix into your resolv.conf and i bet it would work.  

nameserver 208.67.222.222
nameserver 208.67.220.220

---

