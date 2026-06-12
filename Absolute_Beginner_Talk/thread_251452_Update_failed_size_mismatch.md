---
title: "Update failed: size mismatch"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-05
This morning the little orange "updates available" icon told me there were two software updates available to install. So I clicked on all the right buttons to install them, and instead of smooth and flawless installation i got this message:

> 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06.2_all.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06.2_i386.deb)
  Size mismatch

I am completely puzzled. To begin with, what does "size mismatch" mean?

Thanks,
Mimsy

---

### Post by davebgimp on 2006-09-05
Try re-running the update. It's probably a broken download or possibly a bad package update that by now may be repaired.

The mismatch is something along the lines of the file is supposed to be, say, 705k, but Synaptic sees that after downloading it only has 695k, therefore something's not right.

---

### Post by Mimsy on 2006-09-05
I tried rerunning the update, and this time it worked. Thanks for clearing that up!

/Mimsy

---

