---
title: "How to connect to internet via vmware"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-05
I cannot connect to internet via vmware

The vmserver is only localhost

has not been setup for network or remote server i think it is

what i mean is when I start vmware I use localhost not remote server
Cos i said no for vmware to be on network on the setup of vmware

it is xp pro on vmware , using nat settings for internet 

I try to connect vmware machine xp pro, via eth0 connection 

and error = cannot open dev/vment8 op nor such file or directorie

what is causing this problem:confused:

---

### Post by djsroknrol on 2006-08-05
You might try opening a terminal and running this again:

```
sudo ./vmware-install.pl
```

I've had better luck running it "bridged" myself as my Ubuntu box is already connected to the 'net...

You might check out this **[link]("http://ubuntuforums.org/showthread.php?t=183209")**. It's a very through thread on it.

---

