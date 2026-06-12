---
title: "Which anti virus / firewall is best?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-04-27
Any advice re - what anti virus/firewalls are available plus pros and cons?

---

### Post by Happy_Man on 2007-04-27
With Linux, you don't need an antivirus or a firewall; those available for Linux are for making sure you don't forward a virus in an email to a Windows user. :D

---

### Post by starcraft.man on 2007-04-27
Make sure you have a NAT enabled router (it SHOULD be illegal to directly connect anything to the internet unfiltered), other than that no extra firewall or av scanner is needed, nor even a spyware cleaner. For the extra paranoid, I really have always liked avg :)

---

### Post by az on 2007-04-27
Just keep up-to-date with software updates.  You don't need a virus scanner unless you run a mail server.

---

### Post by lamalex on 2007-04-27
Firewall is built into the kernel, if you're looking for a configuration tool so you don't need to learn IP tables configuration you can try firestarer or my personal favourite shorewall. The previous poster was more or less right about the antivirus, clamav is a decent one that's free (freedom).

---

### Post by floke on 2007-04-27
I like threads like this. They remind me of one of the reasons I love Linux :)

---

### Post by James Paige on 2007-04-27
Not really the same think as antivirus, but chkrootkit might be interesting to someone who is wanting to check their Linux system for malware.

---

### Post by psionyk on 2007-04-27
If you're still set on using an anti-virus program, avast also has a free linux edition.

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by whee on 2007-04-27
I know many people would not agree with me on this, but i think it's better to run atleast an extra personal firewall in Linux/Ubuntu.
Here's why i think that.
While ports in Ubuntu are stealth by default, that doesn't mean applications can't make outbound connections to the internet and send private data.
Sure stealthed or blocked ports might block inbound traffic from connecting to services behind those ports and as such prevent exploitation of security bugs/holes in those services, but this isn't necessarily so the other way around.
I like it when i have a firewall that first goes into "learning mode", that way i can see which applications/services make contact with the internet and that way i can choose which applications/connections to allow or deny, yes i know this can also be done with IP tables, but for beginners that comes across like quite a spartan way of doing it.

Also a basic anti-virus application and anti-spyware software can help to give that little extra level of security.

---

### Post by VraiChevalier on 2007-04-27
> **whee said:**
> 
I like it when i have a firewall that first goes into "learning mode", that way i can see which applications/services make contact with the internet and that way i can choose which applications/connections to allow or deny, yes i know this can also be done with IP tables, but for beginners that comes across like quite a spartan way of doing it.


Ditto!

Plus, when I did a port scan at GRC it showed many ports 'closed' not 'stealthed'. I would rather be stealthy

---

### Post by az on 2007-04-28
> **whee said:**
>  but this isn't necessarily so the other way around..

That's only true for a system like windows, where you can not know what is going on.  In linux, you can know at all times what is listening and talking to ports.  It is not really possible to have software talk to the network without you being able to know about it.  This is not so in windows.

In windows, the OS is closed-source and is pretty much a black box.  In Linux, everything is transparent.  

Not to mention that, so long as you stick to ssoftware from the repositories, it is very unlikely that any such spyware/malware is installed on your system in the first place.  Not just anyone can upload packages to the archives.

> **whee said:**
> 

I like it when i have a firewall that first goes into "learning mode", that way i can see which applications/services make contact with the internet and that way i can choose which applications/connections to allow or deny, yes i know this can also be done with IP tables, but for beginners that comes across like quite a spartan way of doing it..

Again, application-based firewalls are only as secure as the underlying OS.  And there are no application-based firewalls in Ubuntu.

> **whee said:**
> 
Also a basic anti-virus application and anti-spyware software can help to give that little extra level of security.

No, it can't.  It adds absolutely nothing to a linux desktop.  You are not taking a risk by avoiding it, you are simply not wasting your time and CPU cycles.  It is not justifiable to install one at this point.

And considering the higher possibility of installing spyware when you install closed-source, thrid-party apps, the fact that they mostly are third-party, closed-source applications, makes installing them a risk in itself.

---

### Post by az on 2007-04-28
> **VraiChevalier said:**
> 
Plus, when I did a port scan at GRC it showed many ports 'closed' not 'stealthed'. I would rather be stealthy

Why?  Unless you disconnect your computer from the network, someone knows you are there.  Every time you visit a web page, the web server knows your IP address.

The difference between "closed" and "stealthed" is a false sense of security.  If you are running something that listens to the network, you will have to 'open' those ports anyway.

---

