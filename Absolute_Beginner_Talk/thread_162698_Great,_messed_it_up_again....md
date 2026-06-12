---
title: "Great, messed it up again..."
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Charax on 2006-04-19
So, I did something stupid, I mounted a Fat32 partition on /home, completely overwriting it and all subdirectories.

Who can tell me what that did? Yup, that's right, it wiped all the user information, and now I can't log in to Gnome, and I'm stuck in a failsafe terminal session.

Any idea how to fix it?

---

### Post by taurus on 2006-04-19
You are not supposed to use fat32 (vfat) as your /home because of permission problems.  If you want to share files between Ubuntu and Windows, create a partition, format it as fat32, and mount it on somewhere like /shares, not /home!
If you wiped everything off on /home, there is nothing else you can do except re-install it.  Hope you have a backup of your important files on /home!!!

---

### Post by Charax on 2006-04-19
Restarting seems to have fixed it, probably because restarting unmounts everything. Seems to not have wiped /home afterall.

That was damned lucky. Ah well, this thread will serve to help those who do as I did.

---

### Post by taurus on 2006-04-19
Sounds like you already have a partition mounted on /home and then you tried to mount another partition with fat32 on /home!!!

---

### Post by IYY on 2006-04-19
Instead of restarting, you could have done

sudo mount -a

to remount all filesystems according to fstab.

---

### Post by wylfing on 2006-04-19
Yeah, it's actually not that likely to be destructive to remount /home like that. Just...bothersome. If your /home was on its own disk partition, you probably could have simply remounted it and all would be well. I'm guessing that's why a reboot helped: it remounted everything the right way again.

Edit: Yep, mount -a would've done it too.

---

