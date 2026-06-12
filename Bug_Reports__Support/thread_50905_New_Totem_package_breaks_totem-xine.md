---
title: "New Totem package breaks totem-xine"
date: 2005-07-21
forum: Bug Reports / Support
---

### Post by Darrena on 2005-07-21
When I installed the new totem package it replaced my Totem-xine with Totem Gstreamer.

Rolling back to 1.1 resolved my problems.

---

### Post by Majlo on 2005-07-21
Same problem ...
[http://ubuntuforums.org/showpost.php?p=264828&postcount=11](http://ubuntuforums.org/showpost.php?p=264828&postcount=11)

---

### Post by ubuntp on 2005-07-21
I think the dependency needs to gets fixed to point to libxine0, you can use [http://www-public.rz.uni-duesseldorf.de/~thpod001/libxine1c2_1.0.1-1ubuntu5_i386.deb](http://www-public.rz.uni-duesseldorf.de/~thpod001/libxine1c2_1.0.1-1ubuntu5_i386.deb) till then. Someone should backport libxine 1.01 *correctly* anyway.

---

### Post by psoleko on 2005-07-23
Well, that explains the horrendously choppy video playback and sound issues.

---

### Post by ions on 2005-07-23
Since the totem update I haven't been able to play any media using totem-xine.

---

### Post by jdong on 2005-07-23
alright, then we need a recompile of totem-xine. I'll file that in. Right now, I'm away from my build machine[s], so can another UBP dev get this done?

---

### Post by infinito on 2005-07-26
[QUOTE=jdong]alright, then we need a recompile of totem-xine. I'll file that in. Right now, I'm away from my build machine[s], so can another UBP dev get this done?[/QUOTE]
 Still doesn't work...

---

### Post by ions on 2005-07-26
[QUOTE=infinito]Still doesn't work...[/QUOTE]

Same here.

---

### Post by jdong on 2005-07-26
This backport has been pulled. Reinstall or downgrade your totem to 1.1.1 from Backports stable.

---

### Post by ions on 2005-07-26
Removed totem-xine then tried to reinstall.  Got this:

> Install these packages without verification [y/N]? y
Get:1 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main totem-xine 1.1.1-0ubuntu3~5.04ubp1 [1031kB]
Get:2 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main totem 1.1.1-0ubuntu3~5.04ubp1 [7612B]
Fetched 1038kB in 3s (265kB/s)

Preconfiguring packages ...
Selecting previously deselected package totem-xine.
(Reading database ... 81739 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libtotem-plparser.so.0', which is also in package libtotem-plparser0
Selecting previously deselected package totem.
Unpacking totem (from .../totem_1.1.1-0ubuntu3~5.04ubp1_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by ions on 2005-07-26
[QUOTE=ions]Removed totem-xine then tried to reinstall.  Got this:[/QUOTE]
 But, after doing that video is working in totem-xine...I dunno.  It's working so I won't complain.

---

