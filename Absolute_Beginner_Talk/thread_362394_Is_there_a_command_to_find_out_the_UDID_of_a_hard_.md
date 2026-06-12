---
title: "Is there a command to find out the UDID of a hard drive?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by jclmusic on 2007-02-15
i need to find out the UDID of a hard drive so i can put in fstab. is there a command for this?

it was so much easier on dapper! removing disks-admin didn't help, either!

---

### Post by hardyn on 2007-02-15
have a search of the old posts, its there i has the same question about 3 weeks ago.

---

### Post by jclmusic on 2007-02-15
lol i searched before posting it and couldn't find anything. i just searched your posts and couldn't find it. can u give me a link?

---

### Post by gollog on 2007-02-15
Try:

ls /dev/disk/by-uuid -lah

- Gollog

---

### Post by jclmusic on 2007-02-15
thanks! :)

---

