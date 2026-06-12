---
title: "Geexbox not seeing Ubuntu Shares"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-11-05
Hey everyone, 

Before my upgrade to Gusty, my Geexbox was able to see my network shares. Now after the upgrade, I cannot see anything! 

Things I can confirm:

Samba shares are visible and accessible through all other PC's in my house (including Windows XP PC's). 

I am able to Ping my Geexbox PC from my Ubuntu machine, so connectivity is verified. 

What would've caused this to stop working?

---

### Post by Dr Small on 2007-11-05
Firewall perhaps ?

---

### Post by homerj742 on 2007-11-05
I HAVE installed Firestarter, as I thought IPtables might be the issue. But I disabled the firewall via Firestarter and I still cannot see the shares. 

Thank you for your reply, do you have any other suggestions?

---

### Post by Dr Small on 2007-11-05
You are referring to seeing the shares. Personally, I have never seen a share in my life.
I always access the Samba share via IP addresses.

Can you access another share by going to:
```
smb://*ipaddress*
```

??

Dr Small

---

### Post by homerj742 on 2007-11-05
Yes, the shares can be accessed via IP address, or by browsing "Network Places" using Windows XP. So they are definitely there and easy to access (via IP and via name).

---

### Post by homerj742 on 2008-05-23
I'm bumping this, as I still have the issue. My workaround was to get some old PC out and install Ubuntu 6.06.2 server on there and have it share out folders with movies. Geexbox sees the shares on Ubuntu 6.06.2 just fine, but not on Ubuntu 7.10. 

But I really don't want a second junk PC running just so I can have a share with media on it for the geexbox.

---

### Post by Fragadelic on 2008-07-03
Are you still having issues?

What does your /etc/samba/smb.conf file look like?

---

