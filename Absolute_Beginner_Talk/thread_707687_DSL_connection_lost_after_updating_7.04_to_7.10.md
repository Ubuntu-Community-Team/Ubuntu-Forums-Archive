---
title: "DSL connection lost after updating 7.04 to 7.10"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by universalis13 on 2008-02-25
I installed Feisty using Wubi which worked fine.
Then I updated to Gutsy and lost my DSL connection.
I have a Iternal error message on startup: failed to initialize HAL!
Also my wired connection is set to roaming.
Any ideas?
I know very little about all this, so please spell it out for me.

Thanks

---

### Post by spiderbatdad on 2008-02-25
If you used wvdial , or one its front ends like kppp or gnome-ppp it is possible your /etc/wvdial.conf file is partially commented out. In 7.04 wvdial accepted lines beginning with semicolons, and indeed the file was written that way. In 7.10 those semicolons are read as comments. So, it may be necessary to edit the file by removing any semicolons at the beginnings of lines. Also eth will compete with the modem, so make sure to disable any ethernet configurations while trying to use the modem.

---

