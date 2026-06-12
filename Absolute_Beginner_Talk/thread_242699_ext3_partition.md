---
title: "ext3 partition"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by xander848 on 2006-08-24
Hey I just converted my fat32 data partition to a ext3 and I can't get it to mount automatically anymore. I looked through postsand edited my fstab but no dice.](*,) Could anyone tell me the proper way to do this.

---

### Post by TFX360 on 2006-08-24
Xander,


Give me the intestins of your /etc/fstab


Kind regards,


TFX

---

### Post by xander848 on 2006-08-24
Well thats kinda the problem. I started with the old fat32 entry and have been looking at posts and documentation and editing that entry so theres nothing for the options, dump, and pass. It's the /dev/hda2 entry.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ext3    [I don't know what to put here]
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda6        /home          ext3    nodev,nosuid       0        2

---

### Post by Jagot on 2006-08-24
I think it should be:

```
/dev/hda2 /media/hda2 ext3 defaults 0 0
```

---

### Post by xander848 on 2006-08-24
Ok I'll try that out. Oh and is there a easy way to test out whether that will work and get it to automount? I have been rebooting but I would assume there would be an easier way...maybe crt+alt+del???

---

### Post by Jagot on 2006-08-24
I could be wrong, but this might do it:

```
sudo mount -a
```

---

### Post by TFX360 on 2006-08-24
Backup the fstab!

cp /etc/fstab /etc/fstab.bck

Then summat like this:

/dev/sda7               /var                    ext3    defaults        1 2

From [Wikipedia.]("http://nl.wikipedia.org/wiki/Mountpoint")

---

### Post by TFX360 on 2006-08-24
> **xander848 said:**
> Ok I'll try that out. Oh and is there a easy way to test out whether that will work and get it to automount? I have been rebooting but I would assume there would be an easier way...maybe crt+alt+del???
Automount should be

```
mount -all
```

Sorry, Ubuntu:


```
sudo mount -all
```

---

### Post by xander848 on 2006-08-24
Ok sweet I got it to automount. Thanks for the help!

---

### Post by TFX360 on 2006-08-24
Your quite welcome, have fun!

---

