---
title: "Networking:  Mapping network drives, and VNC stuff"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-09-03
Okay, so in windows I was easily able to map a network drive and I had my whole house set up using these drives to make backups easier and such, but how do I map a windows shared folder or drive over the network?  Also, i've seen people use the ip address to mount them, but can I use a named constant like the computer's name or something because I have my router on dynamic dhcp.

That also brings up another question.  I have VNC set up finally and I can access windows and linux across my home network just fine, but it makes me use the ip addresses.  When I used vnc in windows I could just type the computer name and it would connect automatically to that computer, but any time I do that in linux it tells me that it can't convert the name into an address.  So is there a way that I can use the named constants instead of the IPs?

Thanks.

---

### Post by GMachine_24 on 2007-09-03
> **CryptiniteDemon said:**
> Okay, so in windows I was easily able to map a network drive and I had my whole house set up using these drives to make backups easier and such, but how do I map a windows shared folder or drive over the network?  Also, i've seen people use the ip address to mount them, but can I use a named constant like the computer's name or something because I have my router on dynamic dhcp.

That also brings up another question.  I have VNC set up finally and I can access windows and linux across my home network just fine, but it makes me use the ip addresses.  When I used vnc in windows I could just type the computer name and it would connect automatically to that computer, but any time I do that in linux it tells me that it can't convert the name into an address.  So is there a way that I can use the named constants instead of the IPs?

Thanks.

Network sharing between Linux and Windows machines is simple. You use Samba.

It's too much to write it out. You'll have to read up on it. But it's fairly easy.

[http://www.samba.org](http://www.samba.org) will get you more information than you ever hoped for. You can also download documentation when you install Samba.

--gm

---

