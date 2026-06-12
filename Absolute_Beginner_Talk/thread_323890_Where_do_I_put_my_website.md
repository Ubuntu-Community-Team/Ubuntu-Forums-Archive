---
title: "Where do I put my website?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2006-12-22
Where do I put my website in apache so that it is on the web?

---

### Post by Beernut on 2006-12-22
The default location is /var/www that is for an out of the box installation.

---

### Post by 4.9 on 2006-12-22
It says I don't have permission to write files in there.

---

### Post by punx45 on 2006-12-22
either A)  use sudo to move things in there, or B) change the permissions on the folder or B.2) change the owner from root to your username.   

I started with A, which got tedious, because you have to sudo edit any files.   so i went to B, and finally B.2 i think.

change permissions = chmod (read man chmod for specifics)
change owner = chown (read man chown for specifics)

---

