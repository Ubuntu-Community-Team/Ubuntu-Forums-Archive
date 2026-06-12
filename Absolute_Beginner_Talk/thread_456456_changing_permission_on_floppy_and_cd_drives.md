---
title: "changing permission on floppy and cd drives"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by sdbkr on 2007-05-27
Hi can anyone tell me how i change the permissions on my cd drives and floppy drives ? at the moment they are read only and the owner is listed as root.

---

### Post by Viskovitz on 2007-05-28
Well, I'm afraid you can't write to a CD-Drive. Or is it a CD-recorder and you're unable to use it?

For the floppy, it should be mounted rw by default. Can you mount it and use it (at least to read)? Can you do a "cat /etc/fstab" and paste the results regarding /media/floppy?

---

### Post by sdbkr on 2007-05-28
hi yes i meant a cdrw, i think the cdrw dives are ok now but have run out of blank disks so won't know till tomorrow. 

re the floppy drive i just get a message saying cannot mount volume 

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

