---
title: "slow internet - IPv6 already off"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Talic on 2007-03-23
Hi, I've been having some problems with my downloading speed, in both the package downloader and in firefox. I have disabled IPv6 in the terminal and verified via the command, I also disabled it in firefox. It seems like the speed wont reach any faster then 50kB/s but it mostly hangs around 20kB/s, I've seen it dip down a lot lower in the packager downloader in the Install/Uninstall program.

I did try using the OpenDNS servers on it since my dns is obtained by the router but that didn't help. I have had this problem before with Mepis. I don't have windows installed on this system so I can't really tell if this is a Linux only problem or not. My main system windows system on the network runs fine I'm positive theres no viruses that could be slowing down my network. My windows machine downloads off of servers I've been testing on around 300-600kB/s but my Linux machine only gets around 50 at the most. I did try speedtest.net on my Linux machine and the upload speed was faster then my download speed.

The system specs are
3000+ Athlon
Epox nForce 3 chipset using the onboard nic
512mb of ram
ATI 9600

Router is a Netgear WGT624v3 wireless router, the computer is hooked in via Ethernet.
Cable modem is a Motorola Surfboard SB5120 and my ISP is Cox.
And this is in 6.10

---

### Post by Talic on 2007-03-25
Any ideas what could be capping the speed like this?

---

### Post by freebird54 on 2007-03-25
Not sure I have a clue here - but HOW did you disable ipv6?  Did you blacklist it or unalias it?

I have never seen a Linux system slow on the net otherwise!  Well - unless my sister is running 120 eMule dloads at the same time as I'm on :D

---

### Post by Talic on 2007-03-26
I disabled it by doing this [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
And I confirmed by doing 

ip a | grep inet6

I did try the OpenDNS servers and that didn't help at all.

The internet is capped so low it makes me think I'm on dial-up when using this pc.

---

### Post by freebird54 on 2007-03-26
Should have done it, though for me it didn't stop the problem till I did the blacklist option (also mentioned there).  However - I didn't check the output, so now I don't remember WHY the first fix didn't work.  IF you

```
gksudo gedit /etc/modprobe.d/blacklist

```

and Add this line:  

```
blacklist ipv6 

```
then you see that it is disabled in the system bootup.

Another thought comes to mind.  How recent is the firmware in your router?  Some of the older ones seem to be forgetting their 'lease' on an address far too often - which could lead to slowdowns a number of ways.  Have you tried flashing its BIOS if so?

---

### Post by lotacus on 2007-03-27
I am having the same problems. By any chance did you install from the edgy DVD ? When I downloaded the CD packages, the network connection was fast (normal). When I later downloaded and burned the DVD package, the internet was at a crawling speed. (never mind installation issues). IPv6 had no effect on the DVD installation. My only assumption is the DVD distro is no longer being actively updated and has poor code. I am "trying" to download all the updates now, very tedious with the slow connection. I got some package failures as well, probably time outs.

If all else fails, i'll just reinstall using the CD packages.

I would really recommend that the Ubuntu dev's either remove the DVD distro or update it.

---

### Post by Talic on 2007-03-28
I think my problem is the ethernet cable, I installed windows xp on it to see if it'll still be slow and it was. I even took out the motherboard and removed the i/o plate to make sure the ethernet cable was getting proper contact and that didn't help.

I even used different routers with the newest firmware and it was still the same. I never thought I'd see a ethernet cable fail like this, very weird stuff.

Anyways thanks for the help, I'll send this mobo back if it keeps doing it, since its a freshly RMA'ed mobo.

---

### Post by Scarlett on 2007-03-28
I noticed I was getting really slow downloads on my last install.  I had IPv6 blacklisted but it didn't seem to help.

Then my computer exploded and I had to reinstall.  The first couple of days I saw extremely fast downloads which were gradually throttled back to the snail's pace I had become accustomed to.

---

### Post by H.E. Pennypacker on 2007-05-28
Talic, tell me about it.  I also have Cox "High Speed" Internet, and we're both in the same position.  I don't know if Cox is to blame, or something else is.  I can't pinpoint anything!

It is very frustrating when you don't know what to attack.  I have recently bought a new router (Linksys WRT54GC), but it didn't solve any problems.

---

