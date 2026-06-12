---
title: "mounting from LiveCD"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-02-03
I need to mount my hda0 and hda1 after booting from ther LiveCD to allow me to copy files from hda0 (old Edgy installation) to hda1 (data partition). This should allow me to reinstall edgy/feisty as my first attempt to upgrade ground to a halt yesterday.
 
tony

---

### Post by taurus on 2007-02-03
There is no such thing as /dev/hda0!  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tchoklat on 2007-02-03
oops sorry. I am not at my Linux PC curently. I am referring to two of my HDD partitions, the one with Linux on and the next one with my Linux data on.

---

### Post by taurus on 2007-02-03
The first one should be /dev/hda1 and the second harddrive should have been /dev/hdb1.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/hda1 /mnt/hdb1
sudo mount -t ext3 /dev/hda1 /mnt/hda1
sudo mount -t ext3 /dev/hdb1 /mnt/hdb1
df -h
```

---

### Post by tchoklat on 2007-02-03
that's great. I actually have two partitions not 2 HDD. I assume that I use hda2 in lieu of hdb1 therefore. Also, are you assuming they are ext3, is that right? As they are!
 
Tony

---

### Post by taurus on 2007-02-03
If you are using the default filesystem, then they are ext3.

```
sudo mkdir /mnt/hda1 /mnt/hda2
sudo mount -t ext3 /dev/hda1 /media/hda1
sudo mount -t ext3 /dev/hda2 /media/hda2
df -h
```

---

### Post by tchoklat on 2007-02-03
thanks  ...

---

### Post by tchoklat on 2007-02-04
Need more guidance please.

I followed Taurus's guide and got an error;

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/hda1
mount: mount point /media/hda1 does not exist
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2 /media/hda2
mount: mount point /media/hda2 does not exist
I need to be able to see/mount hda1 and hda2 so I can copy data from one to the other


Tony

---

### Post by taurus on 2007-02-04
And what's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by tchoklat on 2007-02-04
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1893    15205491   83  Linux
/dev/hda2            4111        7656    28483245   83  Linux
/dev/hda3            1894        4110    17808052+  83  Linux
/dev/hda4            7657        9729    16651372+   5  Extended
/dev/hda5            9601        9729     1036192+  82  Linux swap / Solaris
/dev/hda6            7657        9600    15615117   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by taurus on 2007-02-04
You forgot to create those two new mount points first!

```
sudo mkdir /media/hda1 /media/hda2
```

---

### Post by tchoklat on 2007-02-04
OK I have it working now, and I have copied the data files I require-thanks Taurus.

I have one final question pleae?

I have Edgy on hda1 which I, in error, attempted to upgrade to feisty - it does not work - hence this mess. Can I use the alt CD to reinstall edgy/feisty over the existing contents of that partition?

I would then be back to where I started with operating system on hda1 and data on hda2. Is it that simple????
tony

---

### Post by taurus on 2007-02-04
You can reinstall edgy on /dev/hda1 again if you want.  When you get to the partition part, do the manual and tell the installer to install / on /dev/hda1.  And of course, you want to format it.  However, if you have another partition that you want to mount as /home, then better do it then but DO NOT format it or your /home will be gone.

---

### Post by tchoklat on 2007-02-04
sounds sound!

Will report upon completion.

AGAIN thanks to you dudes who give of your time and patience with we nubes!

thanks Taurus!

---

### Post by taurus on 2007-02-04
You're welcome and good luck.

---

### Post by tchoklat on 2007-02-05
done and working well with a fresh Edgy installation. I tries a fresh Feisty but the install froze at a blue screen so I gave it up and will await the full release!

Tony

---

