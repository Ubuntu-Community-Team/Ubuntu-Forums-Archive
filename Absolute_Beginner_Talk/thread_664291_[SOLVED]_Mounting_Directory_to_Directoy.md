---
title: "[SOLVED] Mounting Directory to Directoy"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-11
I understand that you use mount to "place" a device to a folder. However, if I have two folders on the device (another partition), can I mount one to one folder in home and another to a different home folder?

(Extra partition has my music and pictures. It makes sense to access these from ~/Music and ~/Pictures, right?)

If this is possible, how would I do this automatically? Thanks again!

---

### Post by PeterJS on 2008-01-11
Mounting is an all or nothing proposition, you can't selectively mount parts of a device to different locations.

But to solve your problem you could mount the drive someplace out of the way and then symlink the folders where you want them.

```

ln -s /media/OuttaTheWay/Music ~/Music
ln -s /media/OuttaTheWay/Pictures ~/Pictures

```
 The one limitation of links is that they're no good at overwriting existing files so you'll have to delete the directories in your home folder before trying to create the links to replace them, but this only needs to be done the first time, the links will stick around even if the drive isn't there, they just won't work if they don't have anything to point to.

---

### Post by imaginal on 2008-01-11
That is exactly what I was looking for! But what is the best way to have these folders symlinked anytime the partition is mounted?

---

### Post by Rocket2DMn on 2008-01-11
Those links should stay linked even when the drive isn't mounted.  If you were to click on one with the drive unmounted, it would probably just tell you the directory doesn't exist or the link is broken.

---

### Post by PeterJS on 2008-01-11
That is the best way. The symlinks well be in your home folder, so they won't go away when the parition isn't mounted they just won't work. And when you mount the parition the files on the other end of the links will be there and then the links will work again.

---

