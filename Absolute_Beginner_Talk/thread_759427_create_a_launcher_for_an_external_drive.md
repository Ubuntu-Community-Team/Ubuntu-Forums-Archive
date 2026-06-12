---
title: "create a launcher for an external drive"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-04-19
Can someone help me create a launcher to access my fat32 external drive, and **unmount it automatically on shut down,** to ensure the heads are parked correctly.

I want a mount launcher on the desktop because I don't always want to start the drive, but I want to make sure I do not forget to stop it if I am using it,. when I shut down the main puter. 

At present the drive is /dev/sdc1/ and the mount point is /media/seagate/

so I am thinking "create launcher with command being [COLOR=Blue]sudo mount /dev/sdc1/ /media/seagate [/COLOR]will launch it once I supply my password, but shutting it down automatically is another thing. Appreciate any thoughts.

---

### Post by joshrobinson on 2008-04-19
you can make it auto mount on boot, and auto unmount on shutdown if you want to do that?

---

### Post by sayakb on 2008-04-19
> **tropdoug said:**
> Can someone help me create a launcher to access my fat32 external drive, and **unmount it automatically on shut down,** to ensure the heads are parked correctly.

I want a mount launcher on the desktop because I don't always want to start the drive, but I want to make sure I do not forget to stop it if I am using it,. when I shut down the main puter. 

At present the drive is /dev/sdc1/ and the mount point is /media/seagate/

so I am thinking "create launcher with command being [COLOR=Blue]sudo mount /dev/sdc1/ /media/seagate [/COLOR]will launch it once I supply my password, but shutting it down automatically is another thing. Appreciate any thoughts.

If you are using Gutsy, the drive would be automatically unmounted before shutting down and this action is done by default. You do not have to do anything additional to get it automatically unmounted.

---

### Post by hyperair on 2008-04-19
Make sure you set the launcher to run the command in a terminal, or it won't work. Better yet, why don't you just swap sudo with gksudo?
```

gksudo "mount /dev/sdc1 /media/seagate"

```

That'll pop up a dialog asking you for your password. A graphical sudo if you wish.

As for automatically unmounting, don't worry about that. All mounted filesystems are automatically unmounted before powering off. Regardless of whether it's automatically mounted or not.

Also, when you use /dev/sdc1, don't put the trailing /. /dev/sdc1 is a block device, not a directory. /dev/sdc1/ doesn't exist, but /dev/sdc1 does.

EDIT: Looks like someone beat me to it. Either way, you don't need Gutsy for it. All Linux distros automatically unmount all filesystems before powering off.

---

### Post by tropdoug on 2008-04-24
Gee thanks guys, that solvers it, nice that Linux distros work so much better than MS once you learn a little. 

Sorry it took a while to get back, been busy.

:)

---

