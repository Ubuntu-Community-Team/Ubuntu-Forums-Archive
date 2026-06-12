---
title: "Firefox does not work!!!"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Adntu on 2007-05-04
Hi 
I have newly installed Ubuntu 7.4, all was fine but not the internet, I can update the installed packages using the update manager, but when I try to browse the internet using firefox it does not open any page but google, I checked the console errors and found this one:
" unknown property "_width" declaration dropped"
I checked everything I can think off without success!
would you help!!!

---

### Post by Cypher on 2007-05-04
Just as a guess do the following in a terminal, Applications->Accesories->Terminal
```

sudo ifconfig -a

```
You should see "ETH0" and if that's the only one you see then
```

sudo ifconfig eth0 mtu 1500

```
Try values of 1500, 1400, 1300 until you reach 500 and see if any of that makes any difference..

---

### Post by Adntu on 2007-05-05
Although I know that my network settings are ok, I tried this, and nothing changed, no I am suspecting the firewall, may be it causes the problem, I mean what is called Selinux!!

---

### Post by igknighted on 2007-05-05
> **Adntu said:**
> Although I know that my network settings are ok, I tried this, and nothing changed, no I am suspecting the firewall, may be it causes the problem, I mean what is called Selinux!!

SELinux is only in Fedora/RedHat by default right now AFAIK, so this is probably not your problem.  I would try a couple things.  First, open a terminal and try the "ping" command.  First use it on a website, for example:
```
ping -c 5 www.gentoo.org
```
You can of course pick any website you choose.  The "-c 5" part limits the number of pings, otherwise it would keep going until you hit ctrl+c.  If this works, then your issue is with FF.  If it fails, try pinging a website by IP (I don't know any off the top of my head).  If this works, your issue is with the DNS servers.  If it doesn't, but you can still update, then I am thoroughly confused :).

---

### Post by Adntu on 2007-05-05
I pinged some sites, neither were successful, then I tried to traceroute, it failed too, lastly I checked the DNS as igknighted's suggestion, I found two DNS servers, I removed the first and tried, ooops! it works, it seems that I got fool entry in the DNS, thanks a lot Cypher and igknighted's I appreciate your help.
now I am writing this from Linux-Firefox,  I guess the next time I restart linux it will pick the same wrong DNS, I will try to fix this as well.

---

