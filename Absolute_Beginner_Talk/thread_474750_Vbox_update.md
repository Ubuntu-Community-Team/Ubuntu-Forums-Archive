---
title: "Vbox update"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-15
The new virtualbox update seems to have killed my windows guest machine... 

how can i revert to a previous version of virtualbox (i really dont feel like going thru the 1hour long windows install process again)

---

### Post by starcraft.man on 2007-06-15
> **Tyke91 said:**
> The new virtualbox update seems to have killed my windows guest machine... 

how can i revert to a previous version of virtualbox (i really dont feel like going thru the 1hour long windows install process again)

What exactly do you mean killed the guest? Virtual Box is just a shell, the VDI (image file) can't be modified by updating it. Can you be more specific on the problem?

If its the vboxdrv problem, then you just need to use this:

```
sudo /etc/init.d/vboxdrv setup
```

Run it twice to be sure.

You also have to reinstall the vbox additions over what you previously installed to get them working with the new version. Updating should not break anything though.

---

### Post by Jorge on 2007-06-16
After update (to Vbox 1.4.0) I get this message:
"VERR_SSM_UNSUPPORTED_DATA_UNIT_VERSION"
Then I deleted the snapshot for my Virtual WinXP and restarted OK. 

Maybe this can help you.

---

