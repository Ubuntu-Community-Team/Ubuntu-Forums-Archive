---
title: "How to install without affection Home directory?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by wrybread on 2006-11-29
I need to reinstall Ubuntu, but ideally I'd like to leave my Home directory in tact. Unfortunately it's not on a separate partition.

Is there a way to do that? The Ubuntu installer off the live CD is really bare-bones, doesn't give options to install to a specific partition, at least that I can find. Is there a way to simply install it to the same partition?

---

### Post by tocleora on 2006-11-29
Probably the simplest solution would be to copy the contents of your home folder to a separate partition, CD, DVD, thumb drive, etc. Reinstall and then copy the contents back.  I believe I saw in another thread here where you can copy and keep the permissions and such.  I would guess there's not a way to keep a folder during installation but someone else may know otherwise.

---

### Post by steve.horsley on 2006-11-29
tocleora is right.

To copy and keep flags, permissions etc. is **cp -a src dest**. You could use tar to create one backup file if you prefer.

Before reinstalling, chop the disk into separate / and /home partitions so you don't have the same problem next time.

---

