---
title: "Can't login--Lack of disk space?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by bwolper on 2007-06-24
I tried to install Swift browser.  As it was installing, I got a message that there was not enough disk space.  When I went to restart and login, it didn't let me login.  I got an error messag telling me that it could not login.  One of the possible reasons is lack of disk space.

How can I get in to create more disk space?

---

### Post by steve.horsley on 2007-06-24
You can use a live CD. Mount the offending partition witha command like this:
**sudo mount /dev/hda2 /mnt**
(use the proper device name of course). This mounts the partition at location /mnt in your filesystem so you can see the partition's contents.
Then use **sudo nautilus** to launch a file manager with full rights. Rummage through /mnt looking for things to delete to make space.

---

### Post by bwolper on 2007-06-24
Thanks.  Let me see if I can do that.  I appreciate the quick response>

---

