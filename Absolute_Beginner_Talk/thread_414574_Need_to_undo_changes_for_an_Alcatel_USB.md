---
title: "Need to undo changes for an Alcatel USB"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-04-20
Finally, after months of fighting with an Alcatel USB modem (I could dial-in but not do anything at all)   I broke down and bought a Netopia modem/router.  Now I'm online!!  But everytime I boot up my eth0 connection is innactive.  I presume this is because of the changes/scripts I made while trying to get the Alcatel to auto start at boot.  I have to re-activate eth0 every time.  How do I properly undo those changes?

Also, is there a way to use Nautalis in root mode?

Thanks

---

### Post by lamalex on 2007-04-20
```
gksudo nautilus
``` will launch nautilus as root. By careful  about that, I've seen it cause some problems. exactly what changes did you make?

---

### Post by samadams on 2007-04-20
I followed the howto on the Alcatel at this link:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

I followed the instructions for PPPoA

(In hindsight I noticed that the firmware is listed as for a 330 - I have an old stingray - I thought that was a different model - I've never found any other firmware version other than what is listed on these pages - maybe that's why I could never get it to work)  - Anyway

I can handle deleting the files in my home directory just fine, it's the symbolic links and other stuff I don't know how to undo.

---

### Post by samadams on 2007-04-20
Thanks for the tip.

For some strange reason, on the latest reboot (it was after a system update) the eth0 remains active now on startup.  So I guess it resolved itself.

As for the undo issue, I think it would be nice to know how to properly 'tidy' things up anyway so I don't have that stuff laying around my file structure if I don't need it.

---

