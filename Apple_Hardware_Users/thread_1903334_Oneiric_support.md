---
title: "Oneiric support"
date: 2012-01-02
forum: Apple Hardware Users
---

### Post by kermit666 on 2012-01-02
Hi all,

as a new Mactel 8.1 / Ubuntu 11.10 user I tried to install the drivers from the [PPA]("https://launchpad.net/~mactel-support/+archive/ppa"), but it appears there is still no Oneiric build available (or Natty either for that matter). Is there any reason for this? If it's simply a matter of repackaging the drivers, I would be willing to help, as I'm also a programmer and am reading the Ubuntu dev docs slowly, but I don't know much about drivers...

BTW, so far I've got most of the important functionality working out of the box (I installed utouch (and xserver-xorg-input-synaptics) to get the two-finger scrolling and three-finger window movement working), bluetooth, camera etc. work great, but my wireless is still not recognized and that's a bit of an issue :/

Cheers,
Dražen

---

### Post by crazy bird on 2012-01-02
See attachment. There's a PPA available for most Ubuntu versions.

---

### Post by kermit666 on 2012-01-02
> **crazy bird said:**
> See attachment. There's a PPA available for most Ubuntu versions.

Yeah, but when I [filter for Oneiric]("https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=oneiric") I only get one package:

xserver-xorg-input-synaptics 

None of the other packages can be installed in Oneiric.

---

### Post by crazy bird on 2012-01-02
> **kermit666 said:**
> Yeah, but when I [filter for Oneiric]("https://launchpad.net/~mactel-support/+archive/ppa?field.series_filter=oneiric") I only get one package:
 
xserver-xorg-input-synaptics 
 
None of the other packages can be installed in Oneiric.
 
Maybe that is the only package which needs to be upgraded in order to function properly with Mactel. That's my best guess..

---

### Post by mire on 2012-01-04
In regards to the wireless you may need to install bcmwl-kernel-source. This contains binary-only drivers from Broadcom which the manufacturer for apple's wireless chip set. There is currently no functional open source version of the drivers. Once installed the wireless connection should work.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by kermit666 on 2012-01-17
> **mire said:**
> In regards to the wireless you may need to install bcmwl-kernel-source. This contains binary-only drivers from Broadcom which the manufacturer for apple's wireless chip set. There is currently no functional open source version of the drivers. Once installed the wireless connection should work.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

Thanks, mire. In the mean time I stumbled upon some of the other MBP version's instructions for installing the wireless drivers, though, so here they are for completeness' sake:

```

$ sudo add-apt-repository ppa:mpodroid/mactel
$ sudo apt-get update
$ sudo apt-get install linux-backports-modules-cw-3.2-3.0.0-14-generic 
$ sudo apt-get install firmware-b43-installer

```

Currently enjoying my Mactel Ubuntu :)

---

