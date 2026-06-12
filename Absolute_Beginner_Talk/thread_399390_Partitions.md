---
title: "Partitions"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2007-04-02
I am new to linux , I am building a mail server using Ubuntu 6.10 - I have two 80GB hard drives that I am going to configure as RAID1.

I am allocating my /root partition to have 10GB and my /Swap 6GB - I was wondering about the other 64Gb, should it be /home or /srv or something else? Does it matter?

Thanks for the help

---

### Post by lucaspr on 2007-04-02
You could use about 10 Gb for the '/' partition and 10 Gb for your var partition, the rest for your /home partition. 
It doesn't matter, but it CAN come in handy if you have a different partition for your /home. If you would have to re-install everything, everything will be formatted in the '/' and 'swap' partition. Format these, reinstall and mount your partitions the same way and all your data is save! 

Saved me (or better, my data) a few times now....

---

### Post by Coinnach on 2007-04-02
Thanks mate

---

