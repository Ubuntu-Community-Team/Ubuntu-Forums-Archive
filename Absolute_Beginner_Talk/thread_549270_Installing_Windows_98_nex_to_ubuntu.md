---
title: "Installing Windows 98 nex to ubuntu"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Nussbaum on 2007-09-12
I want to install windows 98. I have a 30 GB linux partition which I downsized to 25 gb. Currently my  partition setup looks like the following(in order):

hda1 [ext3] 25 gb
hda3 [fat32] 5 gb
hda2 [swap] +-1 GB

However when I boot from the windows 98 CD it says it cant find a partition and that it has to format, does this mean it will format the fat32, hda1 or  maybe the whole HD?

Any tips are welcome

---

### Post by bwhitaker on 2007-09-12
Wihout having run through a windows 98 install in quite a while I'm not really sure, but I believe it should give you some choice as to what partition to format.

Did you already format the partition by any chance? or just carve it out in parted or fdisk.



Also you did resise your ext3 file system after doing this right?

```

sudo resize2fs /dev/hda1

```

If you've already resized it it won't do anything and give you a message like this:

```

resize2fs 1.40-WIP (14-Nov-2006)
The filesystem is already 8522474 blocks long.  Nothing to do!

```

---

### Post by Nussbaum on 2007-09-12
> **bwhitaker said:**
> Wihout having run through a windows 98 install in quite a while I'm not really sure, but I believe it should give you some choice as to what partition to format.

Did you already format the partition by any chance? or just carve it out in parted or fdisk.



Also you did resise your ext3 file system after doing this right?

```

sudo resize2fs /dev/hda1

```

If you've already resized it it won't do anything and give you a message like this:

```

resize2fs 1.40-WIP (14-Nov-2006)
The filesystem is already 8522474 blocks long.  Nothing to do!

```

I 'carved it out' and then changed it to fat32 with gparted. I guess that means its formated(thats what I assumed anyway). I didnt use 'sudo resize2fs /dev/hda', only the gparted interface.Maybe switching the partitions around might work (windows maybe looks at the very first partition only)

---

