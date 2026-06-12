---
title: "Problem with Update Manager"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by asvani on 2008-01-17
I'm currently running Ubuntu 7.04 Feisty. The Update manager and the Synaptic Package Manager do not seem to be working. 

When I try "sudo apt-get install" on the terminal, i get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl5170dnlpr needs to be reinstalled, but I can't find an archive for it.

I suspect that it is the printer driver for Brother HL-5170DN  that is causing the problem. Any idea I can solve this.

---

### Post by Cypher on 2008-01-17
How about "sudo apt-get -f install"??

---

### Post by asvani on 2008-01-17
Thanks for the reply but I got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl5170dnlpr needs to be reinstalled, but I can't find an archive for it.

This package is giving me trouble. Any idea how to get around it?

I should also add that when I start Synaptic Package Manager, it gives me

E: The package hl5170dnlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by forestpixie on 2008-01-17
try 

```
sudo dpkg --remove --force-remove-reinstreq hl5170dnlpr
```

and then ttry again to install it

---

### Post by asvani on 2008-01-17
I've tried that and I obtain  

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 149774 files and directories currently installed.)
Removing hl5170dnlpr ...
/var/lib/dpkg/info/hl5170dnlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5170dnlpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5170dnlpr

---

### Post by forestpixie on 2008-01-17
ok - getting a bit beyond me - expected the reinstreq to sort that, but a search found a bug with another brother driver issue - have a look at that 
[https://bugs.launchpad.net/ubuntu/+bug/138378](https://bugs.launchpad.net/ubuntu/+bug/138378)

the last post there appeared to solve it for him

> A simple printer install is proving a real headache. Had above problem where could not remove printer drivers and broke my ability to apt-get or use Synaptic.
[http://ubuntuforums.org/archive/index.php/t-548840.html](http://ubuntuforums.org/archive/index.php/t-548840.html)
Remove all reference to your drivers, (for me it was `mfc440cncupswrapper',) from /var/lib/dpkg/info.
Then run
sudo dpkg --remove --force-remove-reinstreq mfc440cncupswrapper

Now I'm back to square one... *sigh* :(


---

### Post by asvani on 2008-01-17
That worked for me! Thank you so much!

---

