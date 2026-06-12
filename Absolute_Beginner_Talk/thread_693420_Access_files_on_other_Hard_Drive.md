---
title: "Access files on other Hard Drive"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by kraddark on 2008-02-11
I dual-booted Ubuntu 7.10 and windowsxp(NTFS partition).. Now, I have installed WINE and VLC media player.. the problem is how can i access files (like my mp3's,videos) on the other partition which has winxp? when i click on the partition which has winxp it says unable to mount device.. this happens when i open a file using an application in Ubuntu like VLC.. thanks for the help!

---

### Post by kpkeerthi on 2008-02-11
Can you post the outputs of
```

sudo fdisk -l

```
and
```

cat /etc/fstab

```

---

### Post by oedha on 2008-02-11
your win partition supposed to be mounted by default......isn't it ?

---

