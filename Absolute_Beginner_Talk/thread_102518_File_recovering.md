---
title: "File recovering"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-12-12
As recently backed up  my whole hard drive on a new drive with the partitioner found in the installer of the Hoary CD. 

After installing a fresh Hoary, I was able to see the back-up mount point with all the relevant folders etc.

Since Hoary was not giving me the desired results, I copied my back-up back to the old partition. I re-installed Hoary over this "unfresh" or "dirty" installation as reported by the installer. Upon reboot, I am unable to see my back-up on the "safe disk." I can still see the mount point, but the folder is empty. CTRL-H won't show anything either. What have I done wrong and is there a way to get my settings/back-ups back? I esp. need the copy of my chatscripts and PPP scripty to get back online. And of course my repository cache is now gone, worth hours of downloads.

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=GrootBrak]As recently backed up  my whole hard drive on a new drive with the partitioner found in the installer of the Hoary CD. 

After installing a fresh Hoary, I was able to see the back-up mount point with all the relevant folders etc.

Since Hoary was not giving me the desired results, I copied my back-up back to the old partition. I re-installed Hoary over this "unfresh" or "dirty" installation as reported by the installer. Upon reboot, I am unable to see my back-up on the "safe disk." I can still see the mount point, but the folder is empty. CTRL-H won't show anything either. What have I done wrong and is there a way to get my settings/back-ups back? I esp. need the copy of my chatscripts and PPP scripty to get back online. And of course my repository cache is now gone, worth hours of downloads.[/QUOTE]

It sounds like maybe the partition is just not mounted?  If you type
```

$ mount

```
does it show that partition as being mounted?

---

### Post by GrootBrak on 2005-12-21
Yes, it is mounted. It even shows the name "UbuntuBackup" under filesystem, but its emty now. My PC are packed away until I can finish my flooring in the study. Please excuse the slow response.

---

