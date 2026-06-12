---
title: "RHEL Graphics support not enabled"
date: 2011-08-03
forum: Any Other OS
---

### Post by pages on 2011-08-03
Hey all

I'm very new to RHEL but have dabbled with linux in general. I started working for a company lets call them MBI ... and was given my choice of OS , since their servers are all RHEL i chose this as my distro to familiarise myself with it.

system distro being used
```

$  cat /etc/redhat-release
Red Hat Enterprise Linux Workstation release 6.1 (Santiago)

```

My problem is when I try to make the GUI more appealing with fancy effects I get the problem " Accelerated 3D graphics is not available" .
When i go into the system preferences i notice that there is an ATI Catalyst control center however 

```

$ /sbin/lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT216 [Quadro FX 880M] (rev a2)

```

It's a nVidia card that i'm using. I've tried to download the drivers for that which require me to turn off X server and install it in init 3 but also to no avail.

As i said I'm new to most of this but if you could advise me on what to do next or if you need me to type more commands for further help please just ask .

Thanks,
Pages

---

