---
title: "[SOLVED] proxy authentication not working for add/remove programs"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-11-04
I have setup the network proxy in preferences, and set the authentication details for it as well.  It seems to work partially, as it was able to download some, but not all, of the available updates list. (I haven't tried downloading the updates yet as our work network is too slow)

When I try to install new software using add/remove programs, I get this failure message


```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
```




Using Gutsy 7.10

---

### Post by dcstar on 2007-11-05
> **ubnewbie2 said:**
> I have setup the network proxy in preferences, and set the authentication details for it as well.  It seems to work partially, as it was able to download some, but not all, of the available updates list. (I haven't tried downloading the updates yet as our work network is too slow)

When I try to install new software using add/remove programs, I get this failure message

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
```

Using Gutsy 7.10

And you have set up the Proxy settings in Synaptic as well?

---

### Post by ubnewbie2 on 2007-11-05
> **dcstar said:**
> And you have set up the Proxy settings in Synaptic as well?


No, but I have found that apt-get, from the command line, has problems also, and one article on the net, that I read, implies that it can't handle MS ISA proxies - which is what I am forced to use.

Nevertheless, I will try Synaptic's settings tomorrow (when I am back at work).  Thanks for the suggestion

---

### Post by ubnewbie2 on 2007-11-05
> **ubnewbie2 said:**
> No, but I have found that apt-get, from the command line, has problems also, and one article on the net, that I read, implies that it can't handle MS ISA proxies - which is what I am forced to use.

Nevertheless, I will try Synaptic's settings tomorrow (when I am back at work).  Thanks for the suggestion

Yes!!  Synaptic's settings have fixed the problem, even for add/remove programs.

This HAS to be corrected. Ubuntu presents, to the user, a system setting for network proxies, which is ignored by it's own "add/remove programs" application.  Even worse, "add/remove" programs isn't where you need to set the proxy, you have to go to a 3rd app, i.e. Synaptic.

very confusing!

Thanks for your help though

---

