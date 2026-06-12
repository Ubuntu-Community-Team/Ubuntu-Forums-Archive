---
title: "BluRay dumping Ubuntu"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by pgrayf81 on 2007-05-02
Is there a way to dump BluRay movies in Ubuntu 7.04 PS3 by typing a simple command. I tried typing dd if=/dev/cdrom of=/blu-raymovie.iso in the terminal, but it said "permission denied". Does that only work in ydl?

---

### Post by jfinkels on 2007-05-02
> **pgrayf81 said:**
> Is there a way to dump BluRay movies in Ubuntu 7.04 PS3 by typing a simple command. I tried typing dd if=/dev/cdrom of=/blu-raymovie.iso in the terminal, but it said "permission denied". Does that only work in ydl?

You may have to do "sudo dd ..." and type your password when prompted.

---

### Post by jiminycricket on 2007-05-02
It's probably because you don't have permissions to the root directory (/) that you're dumping to, maybe ~/bl.iso would work.  Anyways, sudo should help.

---

