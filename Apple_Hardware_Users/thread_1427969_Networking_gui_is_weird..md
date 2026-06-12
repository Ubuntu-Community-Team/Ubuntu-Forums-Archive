---
title: "Networking gui is weird."
date: 2010-03-12
forum: Apple Hardware Users
---

### Post by overdriv on 2010-03-12
Hi I am new to this forum.  New to Ubuntu.   9.10


I am taking a class in Unix and wanted to really learn both Mac (unix) and Ubuntu (unix). So I installed Ubuntu.  It looks great and I think I will dig out some old PC's and install it on them to bring them back to life. 

I was playing around with the Ubuntu stuff and wanted to be able to surf the web, but when I went to the networking gui, I tried to enter my addresses for my computer, subnet mask and routers and DNS servers.   

1. When choosing "manual" for the address mode, things do not look natural..  like computer address, subnet, router, DNS. 

2. When trying to enter my addresses, the method that is employed is not easy to understand, and when I think I am doing it right the last batch/string of numbers is cut off.  example:

          My address for my computer is 173.8.126.xxx    (xxx = last digits of my address, lets say it is 132)

         What it appears after I go to the next level is  173    8     126         
               (No last three digits. They are dropped off and the periods do not show.)

        This is the same for subnet mask, and  routers  etc.



3. The gui for networking just does not seem to be intuitive to use and seems frustrating when having to use the manual method of inputing the information.

I am probably wrong and it seems like I am being critical, but if I am having a problem maybe others are too. Maybe by speaking up others will be helped.

Nick

---

### Post by nixscripter on 2010-03-12
Being used to it, I use the command line. This should work in both OS X and Ubuntu:

```
sudo ifconfig **interface** 173.3.126.132 up
```

On Ubuntu, interface is eth0, eth1, ... or wlan0, wlan1, ... etc. On the Mac, it's en0, en1, ... etc. You can run **ifconfig -a** to get a list.

DNS servers are in /etc/resolv.conf witth a line that looks like this:

```
nameserver foo
```

Hope this helps.

(By the way, DNS info is stored in an old enemy of mine on the Mac, NetInfo manager. Either edit it with **niutil**, or enable "BSD flat files" for your config to use /etc/reslov.conf. Alas, I forgot how to do either, it was a long time ago...)

---

