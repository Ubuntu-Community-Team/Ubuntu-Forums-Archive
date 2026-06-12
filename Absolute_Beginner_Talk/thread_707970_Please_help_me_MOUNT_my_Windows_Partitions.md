---
title: "Please help me MOUNT my Windows Partitions"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by CosmicSlop on 2008-02-25
I feel like Ive tried everything. Im trying to mount my windows partitions and I cant get it to work. Here is what Im doing;

sudo mkdir /media/Cee

sudo mount /dev/sda1 /media/Cee -t ntfs ro,auto,user,fmask=0111,dmask=0000 0 0

i even tried;

sudo mount /dev/sda1 /media/sda1 ntfs ro,user,fmask=0111,dmask=0000 0 0

Nothing seems to work. 

Help please.

---

### Post by bodhi.zazen on 2008-02-25
Error message ?

Output of ```
mount
```

---

### Post by taurus on 2008-02-25
What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/Cee -o umask=0222
```
Any error message?  If not, see if /dev/sda1 is mounted to /media/Cee with

```
df -h
```

---

### Post by CosmicSlop on 2008-02-25
> **taurus said:**
> What happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/Cee -o umask=0222
```
Any error message?  If not, see if /dev/sda1 is mounted to /media/Cee with

```
df -h
```

This worked but mounted it as root. I cannot edit or save data. What is wrong with my commands. 
When I type them I dont get an error msg, I get the full help text for the mount command and thats it.

TIA.

---

### Post by Rolcol on 2008-02-25
Another way to do it without terminal is to go to Places > Computer.

Right click "Cee" > Mount Volume.

---

### Post by Duck2006 on 2008-02-25
Or you can try this way.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2008-02-25
You need the ntfs-3g driver if you want write access.

---

### Post by CosmicSlop on 2008-02-25
Im sorry. I should have specified. I running 7.10. Doesnt that mean I already have ntfs-3g installed?

---

### Post by Buffalo Soldier on 2008-02-25
here's my fstab entry for my windows partition. hope it helps.

```
# /dev/sda1
UUID=EC284B42284B0B52 /mnt/winxp    ntfs    defaults,umask=007,gid=46 0       1
```

---

### Post by Duck2006 on 2008-02-25
> **CosmicSlop said:**
> Im sorry. I should have specified. I running 7.10. Doesnt that mean I already have ntfs-3g installed?

Yes, if not you can get it from your package manager

---

