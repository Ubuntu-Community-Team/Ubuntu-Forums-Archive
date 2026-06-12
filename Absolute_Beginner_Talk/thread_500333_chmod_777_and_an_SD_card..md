---
title: "chmod 777 and an SD card."
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-07-13
I have an SD Card here. I made a folder in /media called SDcard to mount it to. The device is sdc1, so when I plug it in I do:

sudo mount /dev/sdc1 /media/SDcard

K, fine. Then the folder registers as 1.9gb free which is what the card is. However I can't put anything in the folder. So, I did:

sudo chmod 777 SDcard

However, it seems like the permissions didn't change. Granting it 777 didn't do anything, yet at the CLI I yielded no errors after putting that command in.

What am I doing wrong?

---

### Post by Rocket2DMn on 2007-07-13
For lack of other responses, I'll give my 2 cents.  I don't think flash cards use a filesystem that uses such permissions.  You just need to mount the card in such a way that Ubuntu will let you access it.  This might require unmounting it, running fdisk to get the right data, and adding an entry into /etc/fstab.  Then you can "mount -a"

---

### Post by Roasted on 2007-07-13
I'm just confused by it. Cause when I plug it in, it mounts as "disk" and I can put whatever I wanted to on it. But when I unmount sdc1 from disk and mount it as SDcard, it'll mount but I can't do a damn thing to it. It just doesn't make sense...

---

