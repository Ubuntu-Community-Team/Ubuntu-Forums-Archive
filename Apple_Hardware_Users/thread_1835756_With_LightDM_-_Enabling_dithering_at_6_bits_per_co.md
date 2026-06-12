---
title: "With LightDM - Enabling dithering at 6 bits per colour channel"
date: 2011-08-29
forum: Apple Hardware Users
---

### Post by wersdaluv on 2011-08-29
For the MBA 3,1 and 3,2; the [installation howto for Narwhal]("https://help.ubuntu.com/community/MacBookAir3-2/Narwhal") has instructions to smooth color gradients by adding to "**/etc/gdm/Init/Default**" the following
```
/usr/bin/nvidia-settings -a [gpu:0]/Dithering[DFP-2]=1
/usr/bin/nvidia-settings -a [gpu:0]/DitheringDepth[DFP-2]=1
```

Desktops like 11.10 (Oneric Ocelot) running LigthDM can't use those instructions, though. How could this be done for this DM? 

PS: Reverting to gdm, for some reason, makes graphics slow (but smooth because of the fix mentioned above)

---

