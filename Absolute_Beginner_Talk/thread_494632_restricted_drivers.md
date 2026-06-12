---
title: "restricted drivers"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-07-07
Hi,

My Ubuntu was working fine previously and after I screw up some things I decided to reinstall it. After resintallation I installed all 142 updates. I booted now and I am hardly able to move the mouse. My fan is running fast and clicking on a button gets the action after a long time.

Can someone tell what is screwed up. I hear someone saying about "restrcited drivers" how do I remove this option from Synaptic Package Manager.


thanks,

bluezapper.

---

### Post by mikeyphi on 2007-07-07
Bad luck!
Sounds like possibly a 'bad' install? Did you wipe the HD before/or as part of the new install?

The 'restricted drivers' talk is probably about the graphics drivers that are only activated if you choose. Look under System - Administration - Restricted Drivers Manager.

---

### Post by bodhi.zazen on 2007-07-07
videocard ? Version of Ubuntu (Gutsy ?)

you might want to open a terminal and enter "top" to see what process is the culprit before assuming it is the restricted modules.

To disable the restricted modules System -> Restricted Drivers Manager -> Disable

---

