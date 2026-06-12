---
title: "computer freezes when changing themes"
date: 2010-12-07
forum: Apple Hardware Users
---

### Post by mackaframa85 on 2010-12-07
I have a wubi install on my windows 7 partition.  Every time I try to change my theme in ubuntu 10.04 my computer freezes.

Any help is greatly appreciated, thanks in advance!

---

### Post by bcbc on 2010-12-07
What graphics card do you have? Computer brand/model?

PS when it freezes do you have to hard shutdown or does ALT+SysReq R-S-U-B work to reboot (the latter is preferred)?

---

### Post by mackaframa85 on 2010-12-07
Imac 7,1-Apple

graphics card : ATI,RadeonHD2600

I have to do a hard shutdown because I am unfamiliar with the other option.

Thanks again

---

### Post by bcbc on 2010-12-07
> **mackaframa85 said:**
> Imac 7,1-Apple

graphics card : ATI,RadeonHD2600

I have to do a hard shutdown because I am unfamiliar with the other option.

Thanks again
Alt+SysRq + R-S-U-B (or REISUB) is definitely preferred over hard rebooting for Wubi installs (since if you turn off when the virtual disk (root.disk) is not sync'ed it can be corrupted).
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Not sure about the HD2600 but I see other people have issues with this card on later releases. I cannot vouch for this link, but it might help [http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-ati-radeon-hd-2600-drivers-in-ubuntu.html)

I'd first try the drivers that Ubuntu recommends before downloading them from AMD's site, but maybe you've already done this.

---

### Post by mackaframa85 on 2010-12-07
I have the drivers downloaded from Ubuntu for the graphics card (My desktop effects work).  Also, I cant do the reboot mentioned because I don't have the system requirement key because I have a mac.  Is my system corrupted because I have been hard rebooting?
How can I repair it? 

I also downloaded some theme packs and some will work but others cause system to freeze.  How can I find out which ones will work well with my system?

---

### Post by bcbc on 2010-12-07
> **mackaframa85 said:**
> I have the drivers downloaded from Ubuntu for the graphics card (My desktop effects work).  Also, I cant do the reboot mentioned because I don't have the system requirement key because I have a mac.  Is my system corrupted because I have been hard rebooting?
How can I repair it? 

I also downloaded some theme packs and some will work but others cause system to freeze.  How can I find out which ones will work well with my system?

If the system were corrupted, likely you wouldn't be able to boot. So I don't think that has happened. But it's a risk you take with a hard shutdown. I have no experience with Macs so no idea about how to use RSUB but found this bug [https://bugs.edge.launchpad.net/mactel-support/+bug/262408](https://bugs.edge.launchpad.net/mactel-support/+bug/262408)

---

