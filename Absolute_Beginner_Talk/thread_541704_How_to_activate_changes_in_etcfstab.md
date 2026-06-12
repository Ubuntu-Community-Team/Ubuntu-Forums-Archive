---
title: "How to activate changes in /etc/fstab?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by PetruM on 2007-09-03
I have just changed my /etc/fstab file and added a new NTFS partition.
How can I activate those changes without having to restart the box? :)

---

### Post by tomcheng76 on 2007-09-03
sudo mount -a

---

### Post by PetruM on 2007-09-03
Thanks. :D 
Though, it seems I haven't added that partition correctly in /etc/fstab. Anyway, I've installed the **ntfs-3g** and **ntfs-config** packages and solved the problem. ;)

---

