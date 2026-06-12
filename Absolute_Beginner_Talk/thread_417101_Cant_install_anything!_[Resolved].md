---
title: "Cant install anything! [Resolved]"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-04-21
When I try to install any packages, it gives me this in apt-get
```
The following NEW packages will be installed:
  emerald emerald-themes libemeraldengine0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1574kB of archives.
After unpacking, 4559kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Waiting for headers] 
```
And stays there.

If I use Synaptic it tells me it's downloading 1 out of X files and stays stuck there untill I press cancel.
When I press cancel it gives me an error. Something like "W: Could not...."

Please help me.

---

### Post by markl187ld on 2007-04-21
Lots of the servers are still really busy after the feisty release. Try changing the mirror in synaptic.

---

### Post by aysiu on 2007-04-21
Maybe try different repository mirrors? The Ubuntu servers seem to have become a bit slow around the release of Feisty Fawn on Thursday.

This might help:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by alex-desktop79 on 2007-04-21
I changed from Canadian servers to the Main servers. Seemed to work. :-D Thanks!

---

