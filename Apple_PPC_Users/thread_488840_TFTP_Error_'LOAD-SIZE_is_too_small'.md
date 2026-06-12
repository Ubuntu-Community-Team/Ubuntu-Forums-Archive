---
title: "TFTP Error 'LOAD-SIZE is too small'"
date: 2007-06-30
forum: Apple PPC Users
---

### Post by mentletv on 2007-06-30
I have been given a iMac G3 512Mb RAM, 330mhz. Great. It comes with no Mac OS, instead it has SuSE Linux installed. That's where the good news ends...

1. I have no root password of the box so can't use the SuSE Linux.
2. I can't get the optical drive to read CD's. Am quite sure I burnt them right.
3. I'd like to install ubuntu from a network boot. 

I have set up a TFTP and DHCP. Have put the net boot contents of onto the TFTP server (from [here]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-powerpc/current/images/powerpc/netboot/"))
At the Open Firmware session looks like this:

```
0> boot enet:192.168.0.2,yaboot
CLIENT 192.168.0.3             <-- confirms DHCP has supplied an IP
SERVER 192.168.0.2            <-- my TFTP server
Transfer file:  yaboot
TFTP ERROR response 4 load-size=0 adler32=1
LOAD-SIZE is too small.
```

I believe that it is finding my TFTP server and files. Indeed if I swap 'yaboot' for some large random file I get a progress indicator and lots of transfer activity on my router - and then the same message 'LOAD-SIZE is too small'.

As it happens the Mac does boot into Yaboot off the HD since it was previously installed with SuSE Linux. However I'm not sure that this helps much since if I try to install ubuntu via enet I still get much the same TFTP error (response 4).

I am at a loss, your suggestions are greatly appreciated. Matt.

---

### Post by mentletv on 2007-07-02
I read [this post]("http://hardware.mcse.ms/archive141-2005-7-214602.html") from someone who has seen a similar message upon booting. In their case the USB keyboard was to blame. Can this really be the case?

The keyboard that I have with this mac is a genuine mac keyboard, but doesn't match the mac - wrong shade of blue. Is it likely that finding an alternative keyboard will solve my TFTP problem. Again your thoughts are most welcome.

Matt.

---

### Post by shields on 2008-03-19
I am getting this error on a iBook G4 with NOTHING extra plugged into it while trying to boot from a Ubuntu 7.04 CD.  Has anyone been able to resolve the Open Firmware "LOAD-SIZE is too small" error

---

### Post by oswaldkelso on 2008-03-19
Have you tried holding down the alt/opt key on boot? this should work if the c key fails. and your drive or media is good.

---

