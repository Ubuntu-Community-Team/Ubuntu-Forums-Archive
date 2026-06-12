---
title: "Tring to setup internet and e-mail"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by cdfccf on 2007-09-12
I have installed the alternate vesion of Xubuntu Dapper Drake onto an old IMAC G# 333Mhz computer. I am also a complete newbie to both macs and even more so to linux.

Thus far, I have been unable to setup / configure the computer to reach the internet. can anyone please provide info (newbie info) on exactly what I need to do in order to set this up? In particular, I am trying to connect using the ethernet connection on the computer wired to one of the 4 ports on my linksys WRTP54G VOIP(vonage) router. 

thanks for any help that is offered

---

### Post by jamvegan on 2007-09-12
Welcome to Ubuntu! :-)

I don't remember exactly how things worked in Dapper, and I've never used Ubuntu on a Mac, but on PCs Ubuntu has always found and configured the Ethernet connection for me automatically.

Take a look at System->Administration->Network (may have a slightly different name in Dapper?) and see if you can figure it out from there, or if not, post any more specific questions that you may have.  Does it at least show that you *have* a wired connection (probably labeled eth0), whether or not it's configured?

If you are unable to locate a GUI tool to configure the network, then type the following command in a terminal and post the output here:
```
ifconfig
```

---

### Post by cdfccf on 2007-09-12
I got it!
I was  grasping at straws trying to figure out why, I wasn't ale to retrieve a valid IP address while in DHCP mode, So I swapped out the ethernet cable and .....bam! the system detected and configured itself!

---

### Post by jamvegan on 2007-09-12
A-ha, a physical problem!  Glad to hear you got it working.

---

