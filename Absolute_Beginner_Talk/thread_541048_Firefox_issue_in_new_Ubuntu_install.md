---
title: "Firefox issue in new Ubuntu install"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by raan on 2007-09-02
Hi Folks,
I am a new Linux user, and this is my first post.

I have just installed Ubuntu 7 (DL'd 310807) as the second system on a laptop, the first OS being Win XP Pro. The Win system is a new install as well, and is running in every way as expected under wireless (WEP 64 bit). Both systems are running under DHCP.

Ubuntu is also running as expected in all ways but 1. Wireless is up, and I can access shares on 2 other Win machines on the LAN, and I can ping anywhere on the LAN AND out in the world it seems (all machines utilize the same router hardware (NB620W). 

When I use the included Firefox (2.0.0.3) I can browse ANY address within the Google domain (Web, Images, help and all else), but I seem unable to access any URL outside the Google Domain. Very interesting. I have looked around the Firefox preferences, but find no setting that would cause this kind of restriction (though I may be wrong).

I DL'd Opera (supposedly compatible with Ubuntu, but has .deb as the last extension), and have attempted to install that. I received an error: dependency not satisfiable, so I thought I'd better ask here before I damage what appears to be a good install except for the Firefox issue. I will not be surprised at all to find this is user related.

Any assistance will be greatly appreciated :)

---

### Post by smithman89 on 2007-09-02
if you want to install opera, dont download the package from online.  There is a package in the Synaptic Package Manager for it, and it will install it much neater than using the deb file.  System->Administration->Synaptic Package Manager.  Search opera and install it.  As for the firefox problem, that is really weird, but it may be your wireless setup, it doesnt sound like firefox is having the issue.

---

### Post by aysiu on 2007-09-02
> **smithman89 said:**
> if you want to install opera, dont download the package from online.  There is a package in the Synaptic Package Manager for it, and it will install it much neater than using the deb file.  System->Administration->Synaptic Package Manager.  Search opera and install it.  As for the firefox problem, that is really weird, but it may be your wireless setup, it doesnt sound like firefox is having the issue.
I don't think Opera will be in the repositories unless you add extra repositories. [See?](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=opera&sourceid=mozilla-search)

The easiest way to install Opera is visiting the Opera website, downloading the Ubuntu .deb file, and then double-clicking it.

---

### Post by raan on 2007-09-03
Thanks I'll try that. Interesting that I would have an as expected operating experience in XP on the same machine via the same wireless setup, successfully config wireless for Ubuntu, and not make any changes to Firefox to see what I'm seeing. I know there's nothing wrong with the wireless Router setup because in all I have 5 Win machines cruising on it from different locations in the home. Just one of those wierd computer issues I guess, though I'd be happy learn about it if I have made a mistake in setup. I might revert to Ubuntu 6 and see if I have any issues there. I am keen to become a Linux convert, but I need to have some positive experiences with it to continue with that line of thought.

Time will tell.

Thanks again for your time and assistance :)

---

### Post by skillllllz on 2007-09-04
Hmmm... It could be DNS related. Please post the output of each of these two commands:

```
cat /etc/resolv.conf
``````
dnsdomainname
```

---

