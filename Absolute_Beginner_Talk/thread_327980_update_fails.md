---
title: "update fails"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by dbbd8 on 2006-12-30
aptitude fails to update. It looks to me like resolution of [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gives 1.0.0.0 IP address, but I may be wrong.

Any ideas what I'm doing wrong?

BTW ping works (resolves and pings):
ping us.archive.ubuntu.com
PING mirror.mcs.anl.gov (146.137.96.15) 56(84) bytes of data.

Here's what I see:

dan@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign cdrom://Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main                    Translation-en_US
Ign cdrom://Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restr                   icted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
37% [Connecting to us.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun

---

### Post by Sef on 2006-12-30
Have you updated before or is this your first time updating?

---

### Post by dbbd8 on 2006-12-30
first update after a fresh install.
I also tried removing "us" prefix as I found on some other thread - same issue.

Dan

---

### Post by angkor on 2006-12-30
Can you post your /etc/apt/sources.list?

---

### Post by dbbd8 on 2006-12-30
Here it is:

dan@ubuntu:~$ grep -v '^#' /etc/apt/sources.list


deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted




deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

---

### Post by dbbd8 on 2006-12-31
Turns out several others had similar problems.

The problem is DNS/DHCP setup.
The system was autoconfigured for DHCP.
It recieved the IP address from the [ADSL,DLINK] router, and auto-configured
/etc/resolv.conf to the router address.

This did not work for the DNS lookups apt-get does.
Adding a new entry to resolv.conf [nameserver 4.2.2.3] worked, but
for whatever reason, the resolv.conf keeps getting re-written.

I though its the DHCP reconfiguration, so I changed the /etc/network/interfaces to 
a static IP address - no more DHCP right? well it kind of works,
I now have a static IP address, and still something in Ubuntu keeps re-writing my resolv.conf
with only the router address.

Any ideas how to set up my own addresses in resolv.conf? 
[without installing my own DNS server, really who kills flys with elepant guns]

Thanks and happy new year
Dan

---

### Post by jgubes on 2007-01-02
I've been getting the same problem.  Anybody find a solution for this yet?

---

### Post by dbbd8 on 2007-01-03
The solution is to install resolvconf:
```
sudo apt-get resolvconf
```

and then to add dns servers to
```
/etc/resolvconf/resolv.conf.d/head
```

This way even dhcp rewrites of resolv.conf will include the head contents.
Dan

---

