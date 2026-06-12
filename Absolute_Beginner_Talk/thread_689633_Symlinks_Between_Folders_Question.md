---
title: "Symlinks Between Folders Question"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by TuxBobble on 2008-02-06
I'm having a bit of a problem trying to figure out how to get symlinks to work in Ubuntu 7.10.

I'm trying to link two folders across partitions.  I was able to do it in the file browser but don't know how to make it work in the terminal, which is what I'd prefer since I'm trying to learn the terminal.  The objective is to link the my Pidgin logs between Ubuntu and Windows on my dual-boot machine, since I use logs on both OS's.

I was using the code

```
ln -s .purple/logs/ "/media/sda1/.../.purple/logs/
```

I'm not sure if I'm doing this right.  This does not seem to create the folder properly that is a symbolic link to the /media/sda1/...   Please let me know if I'm doing something wrong.  Thanks a lot.

---

### Post by hyper_ch on 2008-02-06
symlinks need sudo

```

sudo ln -s /path/to/destination /path/to/symlink

```

---

