---
title: "How can I fix Firefox browser"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-30
It started out working fine for several days. Suddenly it will not connect to a lot of websites. For Instance it will not connect to Ubuntu. How do I troubleshoot and fix this?

---

### Post by mhl12 on 2007-01-30
are you connected to the internet?

---

### Post by paydaydaddy on 2007-01-30
> **mhl12 said:**
> are you connected to the internet?

It seems to ping everything fine. When I run traceroute to a site it won't connect to it goes a pretty good ways and then starts saying no reply. I am pretty sure I am connected. I can surf some sights, but not all.

---

### Post by Sef on 2007-01-30
> I am pretty sure I am connected. I can surf some sights, but not all.

If you can get some sites, but not all, then it would be likely the problem is not with Firefox.  Easiest way to check that out is download the Opera browser.  It has a different backend than Firefox.

To download it either:

```
sudo aptitude update
```

```
sudo aptitude install Opera
```

Note: Opera is in multiverse, so you have to [enable that repository]("https://help.ubuntu.com/community/Repositories/Ubuntu").

If you can't do that, then go to the [Opera]("http://www.opera.com/") website.  Under Linux, scroll down and highlight Ubuntu.

Once installed, if you have the same problems, then you know Firefox is not the problem.

---

### Post by paydaydaddy on 2007-01-31
Opera has the same problem.

---

### Post by azurehi on 2007-01-31
I am an absolute unbuntu/linux beginner:  booting from live cd 6.10, accessing firefox leads to no web pages ever loading - firefox indicator runs continuously, never loads a page.  I am using Qwest dsl; blindly looking at networking, etc., shows that DHCP is enabled.  I want to use/install ubuntu but won't install until I can confirm that I can browse.  Any help much appreciated.

---

### Post by jkeyes0 on 2007-01-31
> **paydaydaddy said:**
> Opera has the same problem.

It could have something to do with your nameservers. What is in your /etc/resolv.conf?

---

### Post by azurehi on 2007-01-31
> **jkeyes0 said:**
> It could have something to do with your nameservers. What is in your /etc/resolv.conf?

Working from live cd:  finally found way to view /etc/resolv.conf  the following entries:
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65

---

### Post by azurehi on 2007-03-01
Solved, I believe:  Disabled ipv6.  In firefox, typed about:config, in filter box typed ipv6, right clicked "value", toggled to true; firefox loaded any url and is as fast as in xp.  thanks to several who suggested the ipv6 fix in other threads.

Background:  since my original post, I installed 6.10 and had no difficulty.  Had to reinstall XP recently and when I reinstalled 6.10, firefox would not load pages.  :)

---

