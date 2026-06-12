---
title: "Need help with GAIM 2.0 Beta"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Shoriminimoe on 2006-02-28
I've recently started using ubuntu and I'm trying to update GAIM. I've downloaded the DEB file for it and I type this in the terminal: ```
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
``` then I get this error: ```
dpkg - warning: downgrading gaim from 1:1.5.0-1ubuntu3 to 0:2.0.0beta2-1.
(Reading database ... 93350 files and directories currently installed.)
Preparing to replace gaim 1:1.5.0-1ubuntu3 (using gaim_2.0.0beta2-1_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim_2.0.0beta2-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/gaim.desktop', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0beta2-1_i386.deb

``` How do I fix this?

---

### Post by gord on 2006-02-28
```
 
sudo apt-get remove gaim gaim-data 
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb

```

that might work, allthough iv no idea what-so-ever ;)

---

### Post by majikstreet on 2006-02-28
where's a deb? never seen a deb for gaim2beta..

---

### Post by bwethington on 2006-02-28
[QUOTE=Shoriminimoe]I've recently started using ubuntu and I'm trying to update GAIM. I've downloaded the DEB file for it and I type this in the terminal: ```
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
``` then I get this error: ```
dpkg - warning: downgrading gaim from 1:1.5.0-1ubuntu3 to 0:2.0.0beta2-1.
(Reading database ... 93350 files and directories currently installed.)
Preparing to replace gaim 1:1.5.0-1ubuntu3 (using gaim_2.0.0beta2-1_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim_2.0.0beta2-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/gaim.desktop', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0beta2-1_i386.deb

``` How do I fix this?[/QUOTE]


I have the exact same issue.  I found that I had a gaim process still running, so I killed it and did the remove options as shown above, then installed.  Now it installed just fine, but the icon in app's is gone, and my previous link "gaim" no longer works.  I can't find the app launcher.  

I had previously installed it by forcing a downgrade (not sure why it is considered a downgrade), and it worked fine.  But, then I accidentally did an "apt-get update", then "apt-get upgrade" and it "upgraded" my gaim back down to 1.5...grrrrr. 

Does anyone know where I can find it so that I can creat a launcher for the upgraded gaim?

Brian

---

### Post by bwethington on 2006-02-28
[QUOTE=majikstreet]where's a deb? never seen a deb for gaim2beta..[/QUOTE]

I just downloaded the .rpm from sourceforge and used alien to convert to a .deb....

[http://gaim.sourceforge.net/](http://gaim.sourceforge.net/)

Download .rpm @:
[http://tinyurl.com/bjdjt](http://tinyurl.com/bjdjt)

bw

---

### Post by Shoriminimoe on 2006-02-28
That did the trick:D . Thank you very much.

---

