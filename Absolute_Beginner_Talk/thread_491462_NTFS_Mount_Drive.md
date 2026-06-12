---
title: "NTFS Mount Drive"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by milkolate on 2007-07-03
I isntalled this program that mounts NTFS drives.. so I have my Windows partitions in my Desktop. but when I try to unmount it, it tells me that i'm not privileged to unmount it.. 
What should I do?
Is installing the mounter a bad idea?

---

### Post by pbaumgar on 2007-07-03
Did you use:  sudo umount <drive>?

---

### Post by Rocket2DMn on 2007-07-03
You can't just right click it on the desktop or under Computer, it needs to be unmounted with sudo like pbaumgar said.  Not sure why, but that's just how it is - maybe Gutsy will fix that.

---

### Post by milkolate on 2007-07-03
Ahh.. When I didn't have the mounter installed I was able to unmount/mount the drives with just the right-click

---

