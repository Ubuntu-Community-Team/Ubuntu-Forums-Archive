---
title: "Accessing new fat32 partition"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-04-17
How do I gain access to a fat32 partition on my hard drive from within Ubuntu please?

The partition is identified as /dev/hda8 in GParted, but here's what I get when trying to mount it:

```
$ sudo mount /dev/hda8 /media/hda8
Password:
mount: mount point /media/hda8 does not exist
```

Thanks.

---

### Post by joeblow1102 on 2007-04-17
have you created the folder /media/hda8?

sudo mkdir /media/hda8

---

### Post by ImpelGD on 2007-04-17
Aha, thanks. For some reason I didn't realise that the directories in media are just, um... directories.

:oops:

Thanks for the quick reply. :D

---

### Post by ImpelGD on 2007-04-17
Sorry... next question:

I'd like to permanently have this partition mounted and have write access to it from my own user account. I've tried:

```
$ sudo chown -R david /media/hda8
```

However, I get Operation not permitted messages. Thanks.

---

### Post by joeblow1102 on 2007-04-17
ok, this is where my knowledge is kinda gray.

I know you wanna edit your /etc/fstab file

sudo gedit /etc/fstab

at the bottom, you want /dev/hda8 /media/hda8 fat32 defaults 0 1

this should allow you to access read/write the next time you restart your computer.  if i'm wrong, can someone correct me?

---

### Post by ImpelGD on 2007-04-17
Ok, I'll try that presently. For the moment, I'm doing what I need to on this partition using the super user (so I do have write access with that). Once that's done I'll see if the fstab file change and a restart allows my normal user account to take over ownership.

Thanks for your help.

---

