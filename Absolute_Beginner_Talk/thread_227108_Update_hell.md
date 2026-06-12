---
title: "Update hell"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by jetsta on 2006-08-01
I've just installed Ubuntu 6.06 and am looking for more packages to install.
While trying to update the packages in Synaptic I get :

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

Watching the connection properties it flicks from idle to sending but not receiving. I had to make Firefox use IPv4 instead of IPv6, do I need to set the system to use IPv4 as well? How would I do that? I'm using a DLink   
DSL-G604T router with a DLink DWL-G630 wireless card.

Any help would be appreciated ta.

---

### Post by T700 on 2006-08-01
Sometimes repositories are down for updates, overloaded, or maybe a backhoe cut the fiber on Highway 9 and the backbone's down.  You can:

1.  Ignore the situation and try tomorrow (my choice).

2.  Edit your sources list and put different ones in.  For instance, edit out the "au" and put in "us".  Often that works.

Good luck and welcome to the forums!

Paul

---

### Post by nocturn on 2006-08-01
> **T700 said:**
> Sometimes repositories are down for updates, overloaded, or maybe a backhoe cut the fiber on Highway 9 and the backbone's down.  You can:

1.  Ignore the situation and try tomorrow (my choice).

2.  Edit your sources list and put different ones in.  For instance, edit out the "au" and put in "us".  Often that works.

Good luck and welcome to the forums!

Paul

It's not that the sites are down, they resolve incorrectly for him.
I've seen this many times before with people that have Dlink (based) routers, maybe that's the case now?

--EDIT, I hadn't read the entire post, your router is the cause.
Set a DNS server manually in network properties, the one in the Dlink boxes is broken.  The easiest way to keep this change is to use a static IP address instead of DHCP.

---

### Post by T700 on 2006-08-01
D'oh!  Sorry--I entirely misread the OP.  Thanks for catching that.

Paul

---

### Post by jetsta on 2006-08-01
Thanks for the tips guys, unfortunately they didn't work for me.
I tried the static IP first with no luck, then I edited /etc/apt/sources.list and still no luck. I have tried over a couple of days to update my packages with the same result. Do I need a static IP from my ISP.

Thanks Dave   :(

---

