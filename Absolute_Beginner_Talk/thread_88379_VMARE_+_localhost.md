---
title: "VMARE + localhost"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by markr on 2005-11-10
I've just installed VMWARE with an XP Guest, and need to comminucate with the Linux Guest.

For example.

I've started JBoss on Linus (host),  Using Firefox I can get to the Jboss page by using URL "http://localhost:8080".  I need to do the same sort of thing from the XP guest.

Any thoughts on how to do this?

Mark.

---

### Post by mlomker on 2005-11-10
I don't really understand the question.  What kind of networking did you configure?  I always use bridged networking so that each guest gets its own IP address from the DHCP server...makes things simple.

---

### Post by markr on 2005-11-11
Sorry, didn't explain myself properly.

I have (at least I think I have) set up NAT networking for VMWARE as I want both Host and Guest to be treated as the same machine as far as the outside world is concerned.

ipconfig on my windows guest gives an IP address of 192.168.212.128

ifconfig on my linux host gives an IP address of 192.168.212.1

No problems so far!

I then start JBOSS on the Linux host.  From the guest, I can issue a URL (in IE) of [http://192.168.212.1:8080](http://192.168.212.1:8080) and this shows me the Jboss page - again no problems.

The problem starts when I try and connect an application (on XP) to JBoss (on Linux).

My starter address for the application should be [http://192.168.212.1:8080/GTConnect/WinAcceptor](http://192.168.212.1:8080/GTConnect/WinAcceptor).  This seems to find Jboss as I can see it in the Jboss log.  But here the problem starts.

Not sure which it is,  but either the host or the guest seems to be converting the vmare ip address of 192.168.212.1 back into 127.0.0.1 because my two-way comms with Jboss fails due to a 'localhost' error.

Any thoughts?

Thanks

MArk.

---

### Post by mlomker on 2005-11-11
> Any thoughts?


I don't think I can help because I don't use NAT and I'm not familiar with Jboss.  I have tested Apache and a variety of other applications between guests and hosts but I've only used bridged networking (I let my hardware firewall handle the NAT).

---

