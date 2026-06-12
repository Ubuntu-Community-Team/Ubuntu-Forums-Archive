---
title: "why resolv.conf changes back to original entry?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by liangtp on 2006-04-25
hi, i am new to ubuntu and linux. recently i was having difficulty accessing the internet using ubuntu. then someone was kind enough to ask me to change the /etc/resolv.conf entry of nameserver 192.168.1.1 to 202.188.0.133 (my provider's dns). After that I can successfully access the net. 

However, after I restarted my linux machine, the original entry of the resolv.conf was restored (192.169.1.1) and I cannot access the web unless I change the entry again. 

So how do I make the changes to the resolv.conf permanent? 

Thnaks.

---

### Post by Ensnared on 2006-04-25
This happens because your DHCP-server sends the DNS-servers you're supposed to use. I remember having to edit the actual dhcp-client script to make it stop, but I think that was in Hoary.

In Breezy (and Dapper), what you'll do is edit the file /etc/dhcp3/dhclient.conf:```
sudo gedit /etc/dhcp3/dhclient.conf
```...and look for this line:```
#prepend domain-name-servers 127.0.0.1;
```
Remove the #-mark in front of it and change the IP-address to the actual nameserver you use. If you have two of them (which you probably do), add them both separated by a comma - like this:
```
prepend domain-name-servers 192.168.1.1, 192.168.1.2;
```

EDIT:
Just to elaborate a bit: The #-mark in front of the line means it's commented out, e.g. it will be ignored. Remove the mark and the line will be used.
The "prepend domain-name-servers" does what it says - it puts up the addresses you define before the ones provided by your DHCP-server in your /etc/resolv.conf.
You could also remove "domain-name-servers" from the items listed in the "request"-line in the same file to avoid receiving the DNS-servers at all, but the result will be the same - that is, I just tested adding the servers as described above, but I have not tested what will happen when removing the item from the "request" entry, but it's an educated guess ;)

---

