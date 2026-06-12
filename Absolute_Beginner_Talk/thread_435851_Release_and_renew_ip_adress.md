---
title: "Release and renew ip adress"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by aparigraha on 2007-05-07
Hey.
I've searched the forums without really finding an answer to this probably simple question:

How do I release and renew my ip-adress?

I have so far tried this as root:

```
 ifdown eth0 && ifup eth0

```

This brings my connection down and up again without actually changing my ip.
I'm really new at this... so, anyone please?

---

### Post by Cypher on 2007-05-07
Most DHCP servers usually have a particular lease time. So if you were to try to release/renew before expiration of that lease time, you will be given the same IP address again. Secondly, if you were to indeed go past the expiration time and the IP address previously given to you is available and unclaimed, it will be given to you again.

Thus, it is not strange to get the same IP address across reboots or on a small network.

If you've gotten an IP address, why are you trying to release/renew?

---

### Post by justleen on 2007-05-07
another way is ```
sudo /etc/init.d/networking restart 
```

but the above still applies :)

---

### Post by newlinux on 2007-05-07
```
sudo dhclient
```

I believe will release and renew. But won't necessarily give you a new IP address...

---

### Post by aparigraha on 2007-05-07
Thanks for your replies.
@Cypher

I got ip-banned from my own server for using too many incorrect logins. Now I just need ANY OTHER ip to get in again.

Seems a bit strange to me, that there is now way to get past the DHCP renewal time through.
Fairly easy to force a renewal in Windoze if I remember correctly.

---

### Post by newlinux on 2007-05-07
> **aparigraha said:**
> Thanks for your replies.
@Cypher

I got ip-banned from my own server for using too many incorrect logins. Now I just need ANY OTHER ip to get in again.

Seems a bit strange to me, that there is now way to get past the DHCP renewal time through.
Fairly easy to force a renewal in Windoze if I remember correctly.

In most cases, I believe the server controls the renewal time. You can try and force the lease to expire by doing:

```
sudo dhclient -r
```

and try to obtain a lease again by:

```
sudo dhclient
```

But there is no guarantee the server will erase the lease and assign a completely new IP address. To be sure, if you have access to the server you should be able to expire the lease (I can do this on my router). But none of this guarantees you won't get the same IP address again, but if you do it enough times you probably will (some of this is dependent on how many IP addresses you allow your server to assign and how many of them are alread taken).


dhclient keeps a file of leases that it tries to reuse as well. it's in dhclient.leases. I think that's /var/lib/dhcp/dhclient.leases (not at my linux system right now). So you can see what leases it has... I think you can modify this file. Someone who knows a lot more about this than me can probably help. I would need to be at a linux box to play to know for sure, it's been a while since I did anything with these...

---

### Post by aparigraha on 2007-05-07
Thx newlinux, that did the trick!

I just killed the connection with:

```
ifdown eth0

```

I then went to /var/lib/dhcp3          (why is it called 3 by the way?)
deleted all content in both
dhclient.eth0.leases        AND          dhclient.leases

but I didn't delete the files.

All that remained was
```
ifup eth0
```

and I got a new ip and could immediately connect to my server.

Glad u all helped out... especially newlinux!
THX

---

### Post by nanotube on 2007-05-07
now that your problem is solved it doesn't much matter... 
but just wanted to throw out another possibility. you could just hand-set your ip address to any other ip on your subnet, with command
```
ifconfing ethX inet xxx.xxx.xxx.xxx
```
where ethX is whatever interface you have, and the xxx.xxx is the ip address you want.
anyway, for future reference. :)

---

### Post by aparigraha on 2007-05-07
excellent nanotube... have to try that

---

### Post by Happpiness on 2008-01-01
> **newlinux said:**
> ```
sudo dhclient
```

I believe will release and renew. But won't necessarily give you a new IP address...

Thanks!

---

