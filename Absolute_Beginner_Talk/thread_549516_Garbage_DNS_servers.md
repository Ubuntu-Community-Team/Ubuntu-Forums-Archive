---
title: "Garbage DNS servers"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-12
I finally figured out why my firefox isn't working after 3weeks of trouble shooting. It seems when ever I restart my CPU Ubuntu changes my DNS servers without telling me. Hopefully they get this ironed out before the final release of Gutsy. I tried exploring other post to find a answer but there out of date and offer to many different solutions to the same problem for me to trust there credibility. So rather than waste more time, and  possibly mess things up, I thought I would repost this issue. Any help would be appreciated. Thanks

---

### Post by skymera on 2007-09-12
what DNS does it change to?
whats it suppose to be?

try:
[www.opendns.com](www.opendns.com)

---

### Post by swoll1980 on 2007-09-12
it is supposed to be 68.94.156.1 I set it to this and it works fine but when I restart my cpu it resets it 
to 192.168.0.1 wich is the address of my modem. When I use firefox with these setting it gets hung on looking up "whatever.com" for like 10 seconds before it loads the page

---

### Post by skymera on 2007-09-12
defo try opendns :D
shot my browing speed through the roof!

it changes them to your modem or router?

---

### Post by swoll1980 on 2007-09-12
how do  i use it? If I set it to use this DNS server it will disappear when I restart my cpu. Anyways my DNS works great it only takes like 1 1/2 seconds to load a website the problem is I have to set it up to use my DNS every time I restart my CPU

---

### Post by skymera on 2007-09-12
go to the site:

[www.opendns.com](www.opendns.com)

click linux and atr the top has a complee guide to Ubutnu :D

anything it asks you to edit make sure its unhashed!

it should be permanent, mines stuck.

---

### Post by swoll1980 on 2007-09-12
same problem the only way I can get it to work is if I go into networking and manualy configure DNS everytime I reboot

---

### Post by skymera on 2007-09-12
im puzzled 

sorry :(

---

### Post by p_quarles on 2007-09-12
First we should try to determine whether this is actually a DNS problem or not. My networking interface lists my router as the DNS host, so that''s actually a normal setting. The point is that the router itself is configured with a real DNS. 

If it's a DNS problem, you won't be able to connect with registered domain names, but you *will* be able to connect with the numeric IP addresses. The following IP is for google: 64.233.167.104

Try either pinging it or entering that in your browser.

EDIT: I guess I should add that you'll need to set the DNS back to the modem's address to test this; either manually or by rebooting.

---

### Post by swoll1980 on 2007-09-12
I got it now. I had to type this command into the terminal "sudo chattr +i /etc/resolv.conf " This keeps the file from being written to at boot up. If I want to change DNS settings in the future I have to "sudo chattr -i /etc/resolv.conf " this will make it writable again. Thanks for helping though!!

---

### Post by digen on 2007-09-12
This would be a problem if you were to be on a new or a different network with DHCP. 

The problem is your router is pushing name server entries via DHCP. Your router has a function ideally called `DNS RELAY`.You would like to check your router configuration and change the name servers to OpenDNS or any 3rd party which you may want to use. 

This way you won't have to set a immutable bit to the file. Just my 2 cents !

---

