---
title: "Is extras safe to use without backports"
date: 2005-08-26
forum: Bug Reports / Support
---

### Post by vtec on 2005-08-26
I like to try to stay as close to ubuntu proper as possible. I'm not a big fan of adding a bunch of 3rd party apt-get source because I have gotten burnt doing this with debain and fedora. However there are somethings that i need that are in extras. Is it safe to use extras without backports?

---

### Post by dhjohnson on 2005-08-26
How did you get burned?  I'd say it's pretty darn safe.

---

### Post by ow50 on 2005-08-26
[QUOTE=vtec]I like to try to stay as close to ubuntu proper as possible. I'm not a big fan of adding a bunch of 3rd party apt-get source[/QUOTE]
The new official backports are no longer 3rd party. You can call them *community maintained*  to emphasize their lesser reliability.

[QUOTE=vtec]Is it safe to use extras without backports?[/QUOTE]
Absolutely, but some packages in extras might depend on packages in backports.

---

### Post by vtec on 2005-08-29
[QUOTE=dhjohnson]How did you get burned?  I'd say it's pretty darn safe.[/QUOTE]

Well fedora was the worst. I would have to add a few extra repositories, and in the fedora world not all repositories work well together. I'm new with ubuntu, but it seems its repositories are much more stable. My fedora systems would become unupgradedable between version, and often times whould get a mess of dependances that were conflicting between packages and would casue a dist-upgrade to criple the system tring to fix the dependances. I think i had bad luck with the backports. It seems right after i started using them they started missing packages, and this created dependances problems. So i gess this gets back to my question. Did i just get some bad luck or am i asking for problems by using the backports.

---

