---
title: "editing files"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by fester225 on 2006-07-24
(Kubuntu) In BOINC, I'm supposed to edit gui_rpc_auth.cfg. VI has been unusable. KATE will open, but not change and save it because of permissions.

Is there a visual editor available to edit files?](*,) 

Is it possible to log in as a root user in Kubuntu?](*,)

---

### Post by bensexson on 2006-07-24
execute this command
sudo kate <filename>

this will run kate with root permissions.

---

### Post by aysiu on 2006-07-24
If you're going to run Kate with root privileges: ```
kdesu kate
``` is the proper way to do it.

These two links will explain more:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by SilverBear on 2006-07-24
Great tip!

Thanks, aysiu! I had been unaware of the precise difference --and importance-- of using the gksu and kdesu commands  instead of sudo to initiate a graphical app. I've got those links bookmarked so I can direct others there as well.

You done your Good Deed for the day.

all the best,
SilverBear

---

