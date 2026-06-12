---
title: "[SOLVED] Cannot install/ uninstall software"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by TomDaBomb2u on 2008-04-14
I'm a newbie and made mistake on my system. I was trying to uninstall my JDK via the command line, and entered **sudo apt-get remove java***. When I realized that that's not what I wanted to do, I hit Ctrl+C to cancel the operation. Now, I cannot use aptitude or Update Manager to install anything at all. I keep getting the error: 

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]

Please help!
Thanks!

---

### Post by Inxsible on 2008-04-14
open a terminal and run```
sudo dpkg --configure -a
```

---

### Post by estaticd on 2008-04-14
Try running this:

cd /var/lib/dpkg/updates/
rm *

---

### Post by TomDaBomb2u on 2008-04-14
> **Inxsible said:**
> open a terminal and run```
sudo dpkg --configure -a
```

Thanks for the quick reply. When I did this, I got
**/usr/sbin/dpkg-reconfigure: acidrip is broken or not fully installed**

I tried to reinstall the package acidrip with aptitude, but I keep getting the first error message I reported. 

Any more suggestions?

---

### Post by spiderbatdad on 2008-04-14
Open synaptic package manager.  Click the 'edit' menu. Select 'fix broken packages.'

---

### Post by TomDaBomb2u on 2008-04-14
> **spiderbatdad said:**
> Open synaptic package manager.  Click the 'edit' menu. Select 'fix broken packages.'

Thanks spiderbatdad. Can't open Synaptic at all though. Still getting

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]

---

### Post by Inxsible on 2008-04-14
```
sudo apt-get autoremove acidrip
``` You can re-install acidrip again later once your synaptic starts working.

---

### Post by spiderbatdad on 2008-04-14
You can also try ```
 sudo killall synaptic
sudo killall aptitude
sudo apt-get install -f
```

Make sure update manger is closed.
If those first two commands return..."no process killed," It just means neither was running.

---

### Post by TomDaBomb2u on 2008-04-14
Neither of these options worked. I'm still getting the same error message. :-(

---

### Post by TomDaBomb2u on 2008-04-15
OK guys. Not quite sure what happened, but I decided to go back to the beginning and try each of these suggestions over again, and it works now.

After running
sudo dpkg --configure -a
sudo apt-get install -f

it works fine now.

Thank you all very much!
-Thomas

---

