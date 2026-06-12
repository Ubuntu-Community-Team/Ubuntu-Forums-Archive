---
title: "dual g5: which kernel, and fans"
date: 2006-12-05
forum: Apple PPC Users
---

### Post by bahbo on 2006-12-05
Hi,

I have a dual G5 mac tower that I want to install Linux on.  I have read that the Ubuntu kernel does not support the use of both CPUs in the mac, although when I put in the live cd, it looks to me as if both CPUs are being used (there is a gnome graphical display of cpu usage). I believe the standard Debian kernel does support the use of both CPUs.  So, does anyone know if the Ubuntu Kernel does support dual cpus, or is this a reason to use Debian on the mac over Ubuntu?

Also, is there a problem with the fans running all the time with
Ubuntu?

Also, does anyone know what I should boot into when I insert the install cd? I didn't know whether to go with 'live' or 'live-powerpc64'.  

Thanks,

---

### Post by Torrance on 2006-12-05
Defintiely live-powerpc64 on startup.

I think both CPUs do work - I think multiple processors is enabled in the kernel. I have a single CPU iMac G5 so I'm not completely sure. In any case, its easy to enable both if you were prepared to re-compile the kernel.

Regarding fans: there is nothing wrong with them revving at full speed, but it sure is annoying. To bring them under control either compile a new kernel with "make g5_defconig" or else follow these instructions to force the modules to load on start up:
```

sudo -s
apt-get install powernowd
cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
(ls | cut -d. -f1 | xargs -n1 modprobe) 2>/dev/null
lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
exit
```

---

