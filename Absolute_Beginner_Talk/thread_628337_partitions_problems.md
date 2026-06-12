---
title: "partitions problems"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2007-12-01
hello fellas
i created three partitions

root, home and ext3

but i dont have access to the ext3 partition accept as root
i dont why is like that can anyone help thanks

---

### Post by antoz on 2007-12-01
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

This is a good link about partitions,  you need 1 partition for "/" (ext3) 1 for "swap" (swap) and if you want a separate "home" partition that also is (ext3)

---

### Post by tommcd on 2007-12-01
> **nnamdi said:**
> hello fellas
i created three partitions

root, home and ext3

but i dont have access to the ext3 partition accept as root
i dont why is like that can anyone help thanks

You should have made a swap partition as Antoz said. To get read/write access to the ext3 partition you can do:

sudo chown -R your_user_name:users /ext3

This assumes the ext3 partition is named /ext3 and it's mount point that you chose during the install is /ext3. If you gave it a different name and mount point then substitue that instead.
Also, read through the psychocats site for a good start on ubuntu/linux basics.

---

