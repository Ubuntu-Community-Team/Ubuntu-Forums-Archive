---
title: "[SOLVED] Raid array mounted Read Only,"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by The Avatar of Time on 2008-01-20
Hello, I have a Software Raid 5 array (4 500GB SATA hard drives) that I am using (or will be using) for a media server/storage. When I installed Ubuntu 7.10 I mounted the array to /home/media-server. The trouble is it has mounted itself read only and has owner listed as root (I don't know if that is normal or not). 

My question is how would I make it read/write instead of read only and also where the best place to mount it would be? I originally meant to have it mounted in /home/william/media-server (made a mistake when installing so it is /home/media-server instead). I intend to share this array with a laptop that is running windows vista. I heard from a friend that there might be permission/sharing issues if I mounted the array in the home folder but I have no idea where else to put it, Thanks for any advice.

---

### Post by njparton on 2008-01-20
Most people normally mount under /mnt or /media, although you could mount it anywhere you choose.

You can change the owner and persmissions of the mounted drive by using chown and chmod just like you would a normal folder.  e.g. if your username was bob:

```
sudo chown bob /mnt/drive
sudo chmod u+rwx /mnt/drive
```

Also, post your /etc/fstab file here so we can see how you're mounting it.

---

### Post by The Avatar of Time on 2008-01-20
Hello, thank you for the reply. I have it taken care of now. How would I mark this as solved?

---

### Post by njparton on 2008-01-21
under thread tools at the top I think.

---

