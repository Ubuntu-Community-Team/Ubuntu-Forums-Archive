---
title: "[SOLVED] Official Wiki + Triple Boot with Feisty"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by dmitrijledkov on 2007-09-12
I have Macbook and I have partitioned it using code from Triple boot link from Macbook wiki. I am after Mac OS X, Ubuntu Ultimate, Windows XP combo.

In Triple boot situation they say NOT to creat swap partition.

Will it brake Windows intall if I do? Cause in official wiki you can do that, but they are doing dual boot only.

Or shall install without swap and then use this from triple boot guide:
 
```

dd if=/dev/zero of=/swapfile bs=1024 count=2048000 
mkswap /swapfile
swapon /swapfile 
nano /etc/fstab
/swapfile               swap                    swap    defaults        0 0
```

last line should be in the text file opened in nano

and I can't work out what this is doing and why it is in triple boot guide:

```

sudo su - 
mkdir /mnt/ubuntu 
mount /dev/sda3 /mnt/ubuntu 
mount -t proc none /mnt/ubuntu/proc 
mount -o bind /dev /mnt/ubuntu/dev 
chroot /mnt/ubuntu /bin/bash 
```


Thanks a lot for help. Hopefully I'll be in Ubuntu by the end of this week =D.

BTW Any pitfalls await me if I install the Ultimate Ubuntu and not standard Feisty? Should not be any cause it's still Feisty isn't it?

---

### Post by dmitrijledkov on 2007-09-13
I'll just try and report back.

I have everything backup so nothing to worry about.

---

