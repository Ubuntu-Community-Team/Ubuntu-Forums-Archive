---
title: "flash on firefox"
date: 2008-01-09
forum: Apple PPC Users
---

### Post by tamedcynic on 2008-01-09
I am currently running xubuntu on a bunch of old iMacs (first year they came out) and it's going really well.  I'm a social studies teacher and I have thirty five computers that were almost thrown out by the district.  

I just recently recieved six computers that have been running on OS X (really slowly) and I would like to run either xubuntu or ubuntu on them.  Which is better? 

Also, I was wondering if anyone knew of a way to add Flash to xubuntu. love how lightening-fast it is, but I would love if I could run Flash on Firefox. But if there is a way to get Flash, then I can do online concept mapping, typing tutorials, etc.

---

### Post by BladeMelbourne on 2008-01-10
Xubuntu uses a lot less resources (CPU & RAM) than Ubuntu. Xubuntu is a great choice for older machines.

Adobe hasn't released Flash for PPC Linux, so we're stuck with Gnash. Not many Flash applets work with it however.

To install Gnash, at the command prompt run:

```
sudo apt-get install gnash gnash-common mozilla-plugin-gnash
```

This is from memory, so I hope it's accurate. Restart Firefox after installing.

---

### Post by jcwmoore on 2008-01-12
For the older machines I would recommend xubuntu, also you need to be careful with PPC macs because PPC is no longer officially supported.  I have an iMac G4 (PPC) and run ubuntu fiesty (7.04) on it and it runs very well.  I had trouble upgrading to Gutsy (7.10).  I would recommend that you use version 7.04 or even 6.10 (PPC was officially supported in that version) for your older macs.

---

### Post by bodycoach2 on 2008-01-13
I third the nomination for Xubuntu on those older iMacs. Gnash has worked fine on mine, so far. But then, only tested with Youtube, so I can't make a univeral 'works good' claim on it. I also recommend adding the medibuntu repository, and adding the ppc-codecs. Not sure what all is there, but it helps:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

