---
title: "Fix OSX disk permissions in 9.10"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by lhall on 2009-11-08
I just got my install of 9.10 up and running. It works well overall but i wanted to gain access to my osx disk for certain files but i do not have permissions. I was using the guide posted at the top of this fourm but when i try and change my user groups there i get an error that says:

```
larry@larry-laptop:~$ sudo groupmod -g 20 larry
groupmod: GID '20' already exists

```

Is this step not needed in 9.10, or is there another way to change permissions.

---

### Post by linuxopjemac on 2009-11-08
I added this to my /etc/fstab:

```
/dev/sda2   /mnt/osx   hfsplus   defaults   0   0
```

I can then access the osx partition in /mnt/osx

---

### Post by lhall on 2009-11-08
that didnt work 4 me. does the order in that file matter. i just added that line to the bottom.

---

### Post by linuxopjemac on 2009-11-09
Change /dev/sda2 to your needs, it might be another partition where your version of osx resides...You have to also create the mountpoint if it's not there yet

```
sudo mkdir /mnt/osx
```

---

