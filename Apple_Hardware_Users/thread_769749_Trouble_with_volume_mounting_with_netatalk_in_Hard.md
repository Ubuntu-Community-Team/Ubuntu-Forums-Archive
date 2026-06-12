---
title: "Trouble with volume mounting with netatalk in Hardy"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by ferrous26 on 2008-04-26
Has anyone here been able to set up netatalk with Hardy and share multiple volumes? I can only share my Home Directory right now. When I try to mount my other shared volume I get error telling me the original item cannot be found.

Any suggestions?

---

### Post by zizou007 on 2008-05-28
I am having the same problem with multiple external drives (firewire and usb).  I was able to work around it by sharing the /media directory, where those drives are mounted.  I added the line:

/media  "External Drives" 

to the end of the /etc/netatalk/AppleVolumes.default file.  Now Finder (10.5.2) sees the 'External Drives' folder, and allows navigation of the folders (drives) it contains.

---

