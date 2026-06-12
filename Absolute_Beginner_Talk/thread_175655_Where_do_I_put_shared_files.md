---
title: "Where do I put shared files"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by zudduz on 2006-05-13
Where should I put files that I want to share between users?
Where should I put files that I want to share between computers?

---

### Post by JNowka on 2006-05-13
If you are planning to share files between computers you can make a public folder that is veiwable by all and if you wish can be written to by all.  In doing this all that will be needed is each user to have the password to the network and when they connect they can access the files no matter which computer they are on.

If you do decide to go in this direction, I have found that samba works great for making networks that are accessible by both windows boxes and linux boxes.

---

### Post by mostwanted on 2006-05-13
Another way could be to make a folder somewhere outside /home and set its permissions to be readable and writable by everyone. You can set permissions by right-clicking on the folder in nautilus, selecting properties, the permissions tab, ticking everything.

---

