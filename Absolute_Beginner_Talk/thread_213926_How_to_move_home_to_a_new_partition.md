---
title: "How to move /home to a new partition?"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2006-07-12
Hi,  I've read that is better to have /home in a different partition than /, in order to make new installation (if needed) without loosing the users data. Is there any way to move the /home to a new partition, once the system is already set up with /home inside /? If it's possible, can someone explain how to do it?

Thanks!

---

### Post by jackson0905 on 2006-07-12
edit /etc/fstab.
type :sudo vi /etc/fstab,then ,change the /home mount point <file system>to the partion you want.

---

### Post by maskd on 2006-07-12
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by CalvinChile on 2006-07-12
Thanks Jackson0905 and Maskd for your help, I will give it a try!!

Calvin

---

