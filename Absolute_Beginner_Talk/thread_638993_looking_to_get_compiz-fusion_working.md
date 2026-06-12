---
title: "looking to get compiz-fusion working"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by olavarr on 2007-12-12
Hi, 

I have a Dell XPS gaming PC with Nvidia Geforce 7800 GTX graphic cards. I have installed Ubuntu 7.10 as a virtual machine on the XP pc. I'm trying to get compiz-fusion working. I would love to have the 3d desktop etc. I've install ccm and I tried setting the desktop effects for system startup and it isn't working. My screen goes black and I see a shade of all spectrum colors show up for a second or two and then Ubuntu comes up to login prompt. I log in and I don't see the 3d destop or there isn't any change.
Please any help will be appreciated.



Alpha..........

---

### Post by Nano Geek on 2007-12-12
Are you using the Restricted Nvidia Driver?

---

### Post by Sims2789 on 2007-12-12
Try this:

Copy and paste this into the Text Editor:
```
#!/bin/sh
SKIP_CHECKS=yes compiz --replace
```

Save it as *compizon.sh*

Right-click *compizon.sh*, select Properties, go to Permissions, and check Allow executing file as program.

Double-click it and it should run, unless it's a driver issue.

---

